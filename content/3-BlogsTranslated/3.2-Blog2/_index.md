---
title: "Blog 2"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# **AI-enhanced Subsurface Infrastructure Mapping on AWS**

_By: Santi Adavani, Jacques Guigne, Ryan Qi, Souvik Mukherjee, Srinivas Tadepalli, and Vidyasagar Ananthan — 13 May 2025 — [AWS Batch](https://aws.amazon.com/blogs/hpc/category/compute/aws-batch/), [AWS ParallelCluster](https://aws.amazon.com/blogs/hpc/category/compute/aws-parallel-cluster/), [Customer Solutions](https://aws.amazon.com/blogs/hpc/category/post-types/customer-solutions/), [High Performance Computing](https://aws.amazon.com/blogs/hpc/category/high-performance-computing/), [Thought Leadership](https://aws.amazon.com/blogs/hpc/category/post-types/thought-leadership/)_

Subsurface infrastructure mapping is the process of identifying and visualizing buried structures such as pipes, cables, tanks, and foundations located beneath the surface without excavation. This technology is critical for urban planning, utility maintenance, oil & gas operations, construction safety, and environmental protection. Without accurate subsurface maps, construction projects risk costly delays, dangerous utility strikes, and environmental damage. For example, when Hurricane Ivan damaged an offshore oil platform in 2004, important infrastructure was buried under 35–45 meters of sediment, creating an invisible hazard that traditional mapping techniques could not fully detect.

Through a collaboration between **S2 Labs, Empact AI, and Kraken Robotics**, a breakthrough in subsurface infrastructure mapping has emerged on AWS. The approach combines advanced magnetic imaging with physics-informed AI to deliver unprecedentedly clear images of subsurface structures — especially in scenarios where traditional methods fail. The combination of cloud computing and AI is changing how the industry visualizes and understands critical buried infrastructure.

## Detection methods and limitations

Traditional subsurface imaging uses a range of geophysical techniques, each suited to specific materials and conditions. For example, **electromagnetic methods** detect metallic pipes and cables via conductivity, while **magnetometers** measure variations in Earth’s magnetic field to identify ferrous materials such as steel pipes. **Ground-penetrating radar (GPR)** is particularly effective at imaging concrete structures and geological layers; specialized frequencies can reveal plastic pipes or water-bearing assets because of dielectric contrasts.

Manual interpretation of survey data typically involves 2D signal analysis and basic depth estimation — a fast but approximate approach. Two main challenges arise: first, different subsurface configurations can produce nearly identical sensor responses, making it ambiguous which configuration is correct without additional data. Second, real-world environments contain heterogeneous soils, moisture levels, and material densities that vary over short distances, producing complex signals that traditional algorithms struggle to interpret accurately.

Examining a magnetic survey result, surface measurements show magnetic intensity variations across a 50 m area as illustrated in Figure 1(a). When processed with conventional methods, we obtain a blurred image suggesting a pipe-like structure down to about 5 m, but the result lacks detail (Figure 1(b)). This is where an AI-based approach shows its strength — producing a much sharper image that reveals a pipe-like structure at 1–1.5 m depth (Figure 1(c)). The AI-based result is far more precise while remaining consistent with the original magnetic measurements.

## ![](/images/3-BlogsTranslated/3.2-Blog2/image1.png)

Figure 1. (a) Map view over a 50 m survey patch. (b) Conventional small-square inversion. (c) Deep-learning-based inversion.

## Physics-informed deep learning solution

**S2 Labs** applies physics-informed AI and **AWS high performance computing (HPC)** to solve hard engineering problems across oil & gas, manufacturing, healthcare, and biotech — delivering scientifically accurate results with reduced compute time. S2 Labs partnered with two domain specialists: **Empact AI**, which provides 3D subsurface pipe mapping, and **Kraken Robotics**, which contributes high-resolution underwater imagery via Synthetic Aperture Sonar. This collaboration integrates advanced sonar, 3D subsurface analysis, and AI-driven pattern recognition on **AWS Cloud** to locate and characterize pipeline leaks with higher accuracy and speed.

Our AI approach combines the physics of magnetic fields with deep learning to better interpret what lies underground. By training AI on simulated data that models real-world structures like tanks and pipes, we teach it to “read” magnetic measurements like a map. Using a specialized neural network architecture called **U-Net**, the model learns to translate magnetic signals into crisp images of subsurface structures, identifying not only location but also composition and shape. For technical details, see the recent [research paper](https://www.researchgate.net/profile/Souvik-Mukherjee-3/publication/361686292_High-resolution_imaging_of_subsurface_infrastructure_using_deep_learning_artificial_intelligence_on_drone_magnetometry/links/62d2e42c66bd1654d66a1fa6/High-resolution-imaging-of-subsurface-infrastructure-using-deep-learning-artificial-intelligence-on-drone-magnetometry.pdf) published by S2 Labs.

## Model training

The physics-informed deep learning model was trained on **AWS** by combining high performance compute, scalable data storage, and parallel processing services, as illustrated in the architecture diagram in Figure 2.

Using [**Amazon EC2 instances**](https://aws.amazon.com/ec2/instance-types/c5/), we generated 202,000 3D susceptibility models (each with 226,000 cells) representing many different subsurface scenarios — including pipes at multiple orientations, multiple-pipe configurations, and tanks.

The models were parameterized by domain knowledge and stored as NumPy files in [**Amazon S3**](https://aws.amazon.com/s3/) buckets. S2 Labs’ proprietary magnetostatic solver was containerized and stored in [**Amazon ECR**](https://aws.amazon.com/ecr/) for consistent deployment across compute resources. The solver processed models sequentially from **S3** and wrote the response data back to **S3**.

We also employed distributed computing using [**AWS Batch**](https://aws.amazon.com/batch/) to generate synthetic data, utilizing [**Spot Instances**](https://aws.amazon.com/ec2/spot/) to optimize cost. We used **P4d instances**, each providing eight **NVIDIA A100 GPUs**, to compute field responses at 1,800 measurement points spaced 2 meters apart. The pipeline synchronized data between **Amazon S3** and local storage, trained a **2D U-Net** architecture (500M parameters) for 110 epochs, achieving training loss 0.0018 and validation loss 0.0019. The full computation required 100,000 CPU hours.

## ![](/images/3-BlogsTranslated/3.2-Blog2/image2.png)

Figure 2. Architecture diagram for synthetic data generation and model training on AWS.

## Scalable inference workflow for large magnetic surveys

Our magnetic survey pipeline applies a systematic four-stage workflow to process large surveys efficiently while preserving high-quality, reproducible reconstructions of subsurface infrastructure, illustrated in Figure 3.

Stage 1 — Data Acquisition: Field data collection uses magnetometer systems customized to the survey environment — drone-mounted for airborne surveys, ground systems for land surveys, or underwater systems for marine applications. Surveys follow a systematic grid sampling pattern with consistent sensor heights and transect spacing to ensure uniform coverage of the target area.

Stage 2 — Survey Domain Preparation: Rather than processing the entire survey area at once, we adopt a modular approach by dividing the survey domain into smaller tiles sized to the AI training input. Adjacent tiles include overlap regions that are critical to ensuring smooth transitions in the final reconstruction and avoiding edge artifacts.

Stage 3 — Parallel Processing Architecture: The workflow leverages parallel computing to process many tiles simultaneously, dramatically reducing compute time while preserving consistency with the trained model parameters. This distributed approach efficiently uses compute resources by processing tiles independently. For example, our deployment can process a survey volume of 400 m x 400 m x 60 m in under 5 seconds.

Stage 4 — AI-Based Inference: The trained AI model performs inference on each tile independently, reconstructing subsurface magnetic susceptibility distributions from field magnetic measurements. The reconstructions are then blended smoothly using weighted blending across overlap regions to ensure seamless transitions between neighboring tiles. This modular pipeline enables scalable surveying at any size while maintaining consistent resolution and optimizing memory usage via effective parallel processing, making it practical for real-world applications from infrastructure mapping to geological surveys.

## ![](/images/3-BlogsTranslated/3.2-Blog2/image3.png)

Figure 3. Modular processing workflow for large-scale magnetic surveys.

## Case study: mapping buried offshore well conductors in the Gulf of Mexico

Hurricane Ivan (2004) damaged an offshore oil platform in the Gulf of Mexico, burying well conductors under 35–45 meters of sediment. Initial acoustic imaging in 2022 had some success but remained limited where gas-bearing sediments obscured critical areas. A high-resolution magnetometer array was deployed 3.5 m above the seafloor to detect iron-rich conductors through hydrocarbon-saturated sediment.

The model described earlier successfully mapped conductors buried at 35–45 m depths, revealing a primary conductor bundle and a secondary fragment 40 m northeast of the well bay (see Figure 4). The results show strong discrimination of magnetic signatures even in complex debris fields, verified where possible with borehole locations and acoustic imagery. This demonstrates the power of deep learning in cases where traditional acoustic methods fail.

## ![](/images/3-BlogsTranslated/3.2-Blog2/image4.png)

Figure 4. Plan view (a) and oblique view (b) of relative susceptibility distribution.

## Conclusion

Our work demonstrates how **AI-enhanced magnetic imaging** is transforming subsurface infrastructure mapping across industries — from onshore utilities to deep offshore well conductors. Physics-informed deep learning trained on **AWS** combines HPC resources, scalable storage, and parallel processing services to overcome limitations of traditional magnetic data interpretation.

Through real-world case studies, we demonstrated that deep learning can exceed traditional magnetic interpretation limits and map structures successfully at 40 m depth beneath the seafloor — structures that remained “invisible” to acoustic methods for 18 years.

The impact of this technology spans **oil & gas decommissioning**, **urban utility mapping**, **environmental protection**, and **marine operations**. While results are promising, opportunities remain in **multi-physics integration**, real-time processing, and higher-resolution imaging.

To collaborate or learn more about deployment, please contact us at [**santi@s2labs.co**](mailto:santi@s2labs.co) or [**ryanqi@amazon.com**](mailto:ryanqi@amazon.com).

## Authors

<div style="display:flex; flex-direction:column; gap:1rem;">

<div style="display:flex; align-items:flex-start; gap:1rem;">
  <img src="/images/3-BlogsTranslated/3.2-Blog2/image5.png" alt="Santi Adavani" style="width:120px; height:120px; object-fit:cover; border-radius:8px; flex:0 0 120px; display:block;" />
  <div style="flex:1; min-width:0; line-height:1.45;">
    <strong>Santi Adavani</strong><br/>
    Dr. Santi Adavani is the founder and CEO of <strong>S2 Labs</strong>, a deep-tech startup building <strong>AI</strong> products to accelerate scientific discovery. Prior to S2 Labs, Santi founded and served as CTO of <strong>RocketML</strong>, where he built an <strong>MLOps</strong> platform backed by <strong>HPC</strong>. He also served as Head of Product and AI at <strong>PostgresML</strong>, leading development of an in-memory Postgres-based vector database, and earlier held senior product leadership roles at <strong>Intel</strong>. Santi holds a PhD in Computational Science and Engineering from <strong>University of Pennsylvania</strong>.
  </div>
</div>

<div style="display:flex; align-items:flex-start; gap:1rem;">
  <img src="/images/3-BlogsTranslated/3.2-Blog2/image6.png" alt="Jacques Guigné" style="width:120px; height:120px; object-fit:cover; border-radius:8px; flex:0 0 120px; display:block;" />
  <div style="flex:1; min-width:0; line-height:1.45;">
    <strong>Jacques Guigné</strong><br/>
    Professor Jacques Yves Guigné is a Senior Advisor to <strong>Kraken Robotics</strong> in Newfoundland, Canada. He serves as Chief Scientific Officer of <strong>Subsea Micropiles Ltd.</strong>, which operates in Ireland and the U.K., and is CEO of <strong>Acoustic Zoom Inc.</strong>, a leading geophysical research company. Jacques brings deep experience in acoustic imaging and has made significant contributions to mapping complex seabed features. His scientific achievements include over 80 patents and 70 publications with strong citation counts on ResearchGate. He has been honored in physics with the <strong>Deryck Chesterman and Rayleigh Medals</strong>, holds degrees including a DSc and a PhD, and is recognized as a <strong>Geoscience Canada</strong> member and a director of <strong>PEGNL</strong> (Professional Engineers and Geoscientists Newfoundland and Labrador).
  </div>
</div>

<div style="display:flex; align-items:flex-start; gap:1rem;">
  <img src="/images/3-BlogsTranslated/3.2-Blog2/image7.png" alt="Ryan Qi" style="width:120px; height:120px; object-fit:cover; border-radius:8px; flex:0 0 120px; display:block;" />
  <div style="flex:1; min-width:0; line-height:1.45;">
    <strong>Ryan Qi</strong><br/>
    Ryan has 19 years of experience in multiphysics modeling and simulation, strategy, and business development across industrial and digital domains. At AWS, Ryan is a <strong>Principal Worldwide BD/GTM Leader</strong> focused on simulation technologies and autonomous systems.
  </div>
</div>

<div style="display:flex; align-items:flex-start; gap:1rem;">
  <img src="/images/3-BlogsTranslated/3.2-Blog2/image8.png" alt="Souvik Mukherjee" style="width:120px; height:120px; object-fit:cover; border-radius:8px; flex:0 0 120px; display:block;" />
  <div style="flex:1; min-width:0; line-height:1.45;">
    <strong>Souvik Mukherjee</strong><br/>
    Dr. Souvik Mukherjee is a founding member of <strong>EmPact-AI</strong> and Principal Technical Advisor. His 15+ year career spans energy and technology roles as a geophysicist, data scientist, and product leader. He has received industry recognition such as the <strong>Shell GameChanger (2015)</strong> award and the <strong>URTeC 2019 Best Paper & Innovation</strong> award, among others. He has led and delivered multi-million-dollar projects including commercialization of the award-winning QUANTUM hydraulic-fracture delineation technology for <strong>Carbo Ceramics</strong> and coordinated the <strong>Shell Frontier Exploration Study</strong>, managing a cross-disciplinary team of 15 technical specialists that influenced a $100M lease acquisition strategy.
  </div>
</div>

<div style="display:flex; align-items:flex-start; gap:1rem;">
  <img src="/images/3-BlogsTranslated/3.2-Blog2/image9.png" alt="Srinivas Tadepalli" style="width:120px; height:120px; object-fit:cover; border-radius:8px; flex:0 0 120px; display:block;" />
  <div style="flex:1; min-width:0; line-height:1.45;">
    <strong>Srinivas Tadepalli</strong><br/>
    Srinivas is the <strong>Global HPC Go-to-Market lead at AWS</strong>, responsible for building a comprehensive GTM strategy across HPC and accelerated computing workloads serving commercial and public-sector customers. Previously he worked at <strong>Dassault Systems</strong> and holds a PhD in biomedical engineering.
  </div>
</div>

<div style="display:flex; align-items:flex-start; gap:1rem;">
  <img src="/images/3-BlogsTranslated/3.2-Blog2/image10.png" alt="Vidyasagar Ananthan" style="width:120px; height:120px; object-fit:cover; border-radius:8px; flex:0 0 120px; display:block;" />
  <div style="flex:1; min-width:0; line-height:1.45;">
    <strong>Vidyasagar Ananthan</strong><br/>
    Vidyasagar specializes in high performance computing, numerical simulations, optimization engineering, and software development across industry and academia. At AWS, Vidyasagar is a <strong>Senior Solutions Architect</strong> building predictive models and simulation technologies.
  </div>
</div>

</div>

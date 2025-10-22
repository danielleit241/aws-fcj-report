---
title: "Blog 2"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# **Ánh xạ Cơ sở hạ tầng Dưới lòng đất được Cải tiến bằng AI trên AWS**

_Bởi: Santi Adavani, Jacques Guigne, Ryan Qi, Souvik Mukherjee, Srinivas Tadepalli, và Vidyasagar Ananthan, 13/05/2025, [AWS Batch](https://aws.amazon.com/blogs/hpc/category/compute/aws-batch/), [AWS ParallelCluster](https://aws.amazon.com/blogs/hpc/category/compute/aws-parallel-cluster/), [Customer Solutions](https://aws.amazon.com/blogs/hpc/category/post-types/customer-solutions/), [High Performance Computing](https://aws.amazon.com/blogs/hpc/category/high-performance-computing/), [Thought Leadership](https://aws.amazon.com/blogs/hpc/category/post-types/thought-leadership/)_

Subsurface infrastructure mapping là quá trình xác định và trực quan hóa các cấu trúc bị chôn vùi như đường ống, cáp, bồn chứa, và nền móng tồn tại bên dưới bề mặt mà không cần khai quật. Công nghệ này rất quan trọng trong quy hoạch đô thị, bảo trì tiện ích, vận hành dầu khí, an toàn xây dựng và bảo vệ môi trường. Không có bản đồ hạ tầng ngầm chính xác, các dự án xây dựng có nguy cơ bị trì hoãn tốn kém, va chạm nguy hiểm với tiện ích, và gây hại môi trường. Ví dụ, khi bão Ivan làm hỏng một giàn khoan dầu ngoài khơi năm 2004, nó để lại hạ tầng quan trọng bị chôn dưới 35–45 mét trầm tích, tạo ra mối nguy vô hình mà các kỹ thuật bản đồ truyền thống không thể phát hiện đầy đủ.

Nhờ sự hợp tác giữa **S2 Labs, Empact AI và Kraken Robotics**, một bước đột phá trong subsurface infrastructure mapping đã xuất hiện trên AWS. Cách tiếp cận này kết hợp magnetic imaging tiên tiến với physics-informed AI, mang lại hình ảnh rõ nét chưa từng có về các cấu trúc ngầm – đặc biệt trong điều kiện mà phương pháp truyền thống thất bại. Sự kết hợp sức mạnh cloud computing và AI đang thay đổi cách ngành công nghiệp hình dung và hiểu về hạ tầng ngầm quan trọng.

## **Phương pháp phát hiện dưới bề mặt và những hạn chế**

Hình ảnh dưới bề mặt truyền thống sử dụng nhiều kỹ thuật địa vật lý khác nhau, mỗi kỹ thuật phù hợp với những loại vật liệu và điều kiện cụ thể. Ví dụ, **electromagnetic methods** phát hiện các đường ống kim loại và cáp thông qua độ dẫn điện của chúng, trong khi **magnetometers** đo sự biến thiên của từ trường Trái Đất để xác định các vật liệu có từ tính như ống thép. **Ground-penetrating radar (GPR)** đặc biệt hiệu quả trong việc tạo ảnh các công trình bê tông và các cấu trúc địa chất, và các tần số chuyên dụng có thể phát hiện các đường ống nhựa hoặc tài sản chứa nước nhờ vào đặc tính điện môi của chúng.

Việc diễn giải thủ công dữ liệu hình ảnh thường chỉ bao gồm phân tích tín hiệu địa vật lý 2D và tính toán độ sâu cơ bản – nhanh nhưng chỉ mang tính xấp xỉ. Có hai thách thức chính: Thứ nhất, đôi khi những cách sắp xếp khác nhau của các vật thể ngầm có thể tạo ra kết quả giống hệt nhau trên các công cụ phát hiện, khiến chúng ta không thể biết được cấu hình nào đúng nếu không có dữ liệu bổ sung. Thứ hai, môi trường thực tế có nhiều loại đất, mức độ ẩm và mật độ vật liệu thay đổi trong phạm vi ngắn, tạo ra các tín hiệu phức tạp mà các thuật toán truyền thống khó xử lý chính xác.

Quan sát kết quả khảo sát từ tính, chúng ta thấy các phép đo bề mặt cho thấy cường độ từ trường thay đổi trong một khu vực rộng 50 mét, như minh họa trong Hình 1(a). Khi xử lý dữ liệu này bằng phương pháp truyền thống, chúng ta thu được hình ảnh sơ bộ về một cấu trúc giống như đường ống kéo dài xuống khoảng 5 mét, nhưng hình ảnh mờ và thiếu chi tiết (Hình 1(b)). Đây chính là nơi phương pháp dựa trên **AI** cho thấy ưu thế – nó mang lại hình ảnh rõ ràng hơn nhiều, hiển thị một cấu trúc giống đường ống nằm ở độ sâu từ 1 đến 1,5 mét dưới bề mặt (Hình 1(c)). Nhờ vậy, phương pháp AI xác định vị trí chính xác hơn nhiều, đồng thời vẫn duy trì tính nhất quán với các phép đo từ tính ban đầu.

## ![](/images/3-BlogsTranslated/3.2-Blog2/image1.png)

_Hình 1\. (a) Chế độ xem bản đồ trên một phần khảo sát rộng 50m. (b) Phương pháp đảo ngược bình phương nhỏ thông thường. (c) Phương pháp đảo ngược dựa trên học sâu._

## **Giải pháp deep learning dựa trên vật lý**

**S2 Labs** ứng dụng **physics-informed AI** và **AWS high performance computing (HPC)** để giải quyết các bài toán kỹ thuật phức tạp trong các lĩnh vực dầu khí, sản xuất, chăm sóc sức khỏe và công nghệ sinh học, mang lại các giải pháp vừa đảm bảo tính chính xác khoa học vừa rút ngắn thời gian tính toán. **S2 Labs** đã hợp tác với hai đối tác chuyên biệt: **Empact AI**, cung cấp bản đồ đường ống ngầm 3D, và **Kraken Robotics**, đóng góp hình ảnh dưới nước độ phân giải cao thông qua hệ thống **Synthetic Aperture Sonar**. Sự hợp tác này tích hợp công nghệ sonar tiên tiến, phân tích dưới bề mặt 3D và nhận dạng mẫu dựa trên AI thông qua **AWS Cloud** để xác định và định vị nguồn rò rỉ đường ống với độ chính xác và tốc độ cao hơn.

Phương pháp **AI** của chúng tôi kết hợp vật lý của từ trường với **deep learning** để hiểu rõ hơn những gì nằm dưới lòng đất. Bằng cách huấn luyện **AI** với dữ liệu mô phỏng dựa trên các cấu trúc thực tế như bồn chứa và đường ống, chúng tôi có thể dạy nó “đọc” các phép đo từ trường như đọc một bản đồ. Sử dụng một loại **neural network** đặc biệt gọi là **U-Net**, AI học cách chuyển đổi các tín hiệu từ trường này thành hình ảnh rõ nét của các cấu trúc ngầm, cho chúng ta biết không chỉ vị trí mà còn cả thành phần và hình dạng của chúng. Nếu bạn quan tâm đến chi tiết kỹ thuật, hãy xem bài [báo khoa học](https://www.researchgate.net/profile/Souvik-Mukherjee-3/publication/361686292_High-resolution_imaging_of_subsurface_infrastructure_using_deep_learning_artificial_intelligence_on_drone_magnetometry/links/62d2e42c66bd1654d66a1fa6/High-resolution-imaging-of-subsurface-infrastructure-using-deep-learning-artificial-intelligence-on-drone-magnetometry.pdf) gần đây do **S2 Labs** công bố.

## **Model training**

Mô hình **physics-informed deep learning** được huấn luyện trên **AWS** bằng cách kết hợp các tài nguyên **high performance computing**, hệ thống lưu trữ dữ liệu, và các dịch vụ xử lý song song, như minh họa trong sơ đồ kiến trúc ở Hình 2\.

Sử dụng [**Amazon EC2 instances**](https://aws.amazon.com/ec2/instance-types/c5/), chúng tôi đã tạo ra 202.000 mô hình 3D susceptibility (mỗi mô hình gồm 226.000 cells) đại diện cho nhiều kịch bản dưới lòng đất khác nhau – bao gồm đường ống với nhiều hướng khác nhau, các cấu hình nhiều đường ống, và bồn chứa.

Các mô hình sau đó được tham số hóa dựa trên kiến thức chuyên ngành và lưu trữ dưới dạng file **NumPy** trong [**Amazon S3**](https://aws.amazon.com/s3/) **buckets**. Ứng dụng **magnetostatic solver** độc quyền của **S2 Labs** được container hóa và lưu trữ trong [**Amazon ECR**](https://aws.amazon.com/ecr/) để triển khai đồng nhất trên các tài nguyên tính toán. Solver này xử lý tuần tự các mô hình từ **S3**, rồi lưu kết quả phản hồi trở lại **S3**.

Chúng tôi cũng triển khai **distributed computing** bằng [**AWS Batch**](https://aws.amazon.com/batch/) để sinh dữ liệu, sử dụng [**Spot Instances**](https://aws.amazon.com/ec2/spot/?gclid=Cj0KCQjwhYS_BhD2ARIsAJTMMQa9Sc6yPFqEXZxaC3abEhueNkk1qFM4qaB-yWG02QRugH5RtwK47OUaAobDEALw_wcB&cards.sort-by=item.additionalFields.startDateTime&cards.sort-order=asc&trk=46b0eefc-8c98-474e-8590-b407d7fe3181&sc_channel=ps&ef_id=Cj0KCQjwhYS_BhD2ARIsAJTMMQa9Sc6yPFqEXZxaC3abEhueNkk1qFM4qaB-yWG02QRugH5RtwK47OUaAobDEALw_wcB:G:s&s_kwcid=AL!4422!3!651751059279!e!!g!!ec2%20spot%20instances!19852662173!145019250457) nhằm tối ưu chi phí. Chúng tôi dùng **P4d instances**, mỗi instance cung cấp tám **NVIDIA A100 GPUs** để tính toán phản hồi từ trường tại 1.800 điểm đo với khoảng cách 2 mét. Pipeline đồng bộ dữ liệu giữa **Amazon S3** và bộ nhớ cục bộ, huấn luyện kiến trúc **2D U-Net** (500 triệu tham số) trong 110 **epochs**, đạt **training loss** 0.0018 và **validation loss** 0.0019. Toàn bộ tính toán yêu cầu 100.000 **CPU hours**.

## ![](/images/3-BlogsTranslated/3.2-Blog2/image2.png)

_Hình 2\. Sơ đồ kiến ​​trúc để tạo dữ liệu tổng hợp và đào tạo mô hình trên AWS._

## **Quy trình làm việc để suy luận các cuộc khảo sát từ trường quy mô lớn**

Pipeline xử lý khảo sát từ tính của chúng tôi áp dụng một **quy trình bốn giai đoạn có hệ thống** để xử lý các khảo sát quy mô lớn một cách hiệu quả, đồng thời vẫn duy trì khả năng tái tạo chất lượng cao các cấu trúc hạ tầng ngầm, minh họa trong Hình 3\.

**Stage 1 – Data Acquisition:** Việc thu thập dữ liệu hiện trường bắt đầu bằng các hệ thống **magnetometer** được tùy chỉnh theo môi trường khảo sát – gắn trên drone cho khảo sát trên không, hệ thống mặt đất cho khảo sát trên đất liền, hoặc hệ thống dưới nước cho ứng dụng biển. Các khảo sát tuân theo lưới mẫu có hệ thống với độ cao cảm biến và khoảng cách đường khảo sát nhất quán để đảm bảo vùng mục tiêu được bao phủ đồng đều.

**Stage 2 – Survey Domain Preparation:** Thay vì xử lý toàn bộ khu vực khảo sát cùng lúc, chúng tôi áp dụng phương pháp mô-đun bằng cách chia miền khảo sát thành các ô nhỏ hơn, phù hợp với kích thước huấn luyện của mô hình AI. Các ô liền kề có vùng chồng lấn, rất quan trọng để đảm bảo sự chuyển tiếp mượt mà trong tái tạo cuối cùng và tránh hiện tượng nhiễu ở rìa.

**Stage 3 – Parallel Processing Architecture:** Quy trình tận dụng **parallel computing** để xử lý đồng thời nhiều ô, từ đó giảm đáng kể thời gian tính toán trong khi vẫn đảm bảo tính nhất quán với các tham số của mô hình đã huấn luyện. Cách tiếp cận phân tán này giúp sử dụng hiệu quả tài nguyên tính toán thông qua xử lý ô độc lập. Ví dụ, triển khai của chúng tôi có thể xử lý dữ liệu khảo sát kích thước **400 m x 400 m x 60 m** trong chưa đến **5 giây**.

**Stage 4 – AI-Based Inference:** Mô hình AI đã huấn luyện thực hiện **inference** trên từng ô một cách độc lập, tái tạo phân bố **magnetic susceptibility** dưới bề mặt từ các phép đo từ trường. Các bản tái tạo sau đó được kết hợp liền mạch bằng phương pháp **weighted blending** tại các vùng chồng lấn, đảm bảo sự chuyển tiếp mượt mà giữa các ô liền kề để tạo ra kết quả cuối cùng thống nhất. Quy trình mô-đun này cho phép khả năng mở rộng cho khảo sát ở mọi kích thước, đồng thời duy trì độ phân giải nhất quán và tối ưu hóa việc sử dụng bộ nhớ nhờ xử lý song song hiệu quả, khiến nó trở nên khả thi trong các ứng dụng thực tế từ bản đồ hạ tầng ngầm đến khảo sát địa chất.

## ![](/images/3-BlogsTranslated/3.2-Blog2/image3.png)

_Hình 3\. Quy trình xử lý mô-đun cho các cuộc khảo sát từ tính quy mô lớn._

## **Nghiên cứu điển hình: phát hiện đường ống dẫn dầu khí dưới nước ở Vịnh Mexico**

Cơn bão **Hurricane Ivan (2004)** đã làm hư hại một giàn khoan dầu ngoài khơi ở Vịnh Mexico, chôn vùi các **well conductors** dưới lớp trầm tích dày 35–45 mét. Hình ảnh **acoustic imaging** ban đầu vào năm 2022, dù có phần thành công, nhưng vẫn bị hạn chế do trầm tích chứa khí che khuất các khu vực quan trọng. Một mảng **magnetometer** độ phân giải cao được triển khai cách đáy biển 3,5 mét để phát hiện các conductors giàu sắt xuyên qua lớp trầm tích bão hòa hydrocarbon.

Mô hình mà chúng tôi đã mô tả ở các phần trước đã lập bản đồ thành công các conductors bị chôn vùi ở độ sâu 35–45 mét, hé lộ một bó conductor chính và một đoạn mảnh vỡ thứ cấp nằm cách **well bay** 40 mét về phía đông bắc (như minh họa trong Hình 4). Kết quả cho thấy khả năng phân biệt vượt trội các **magnetic signatures** trong trường hợp có nhiều mảnh vỡ phức tạp, được xác minh qua các điểm khoan và hình ảnh acoustic khi có thể. Điều này chứng minh hiệu quả của **deep learning** trong những trường hợp mà các phương pháp acoustic truyền thống thất bại.

## ![](/images/3-BlogsTranslated/3.2-Blog2/image4.png)

_Hình 4\. Hình chiếu bằng (a) và hình chiếu xiên (b) của phân bố độ nhạy tương đối._

## **Kết luận**

Công trình của chúng tôi cho thấy cách **AI-enhanced magnetic imaging** đang thay đổi lĩnh vực **subsurface infrastructure mapping** trên nhiều ngành, từ các tiện ích nông trên đất liền đến các **offshore well conductors** sâu dưới biển. Mô hình **physics-informed deep learning** được huấn luyện trên **AWS** bằng cách kết hợp các tài nguyên **high performance computing**, hệ thống lưu trữ dữ liệu và các dịch vụ xử lý song song.

Thông qua các **case study** thực tế, chúng tôi đã chứng minh rằng **deep learning** có thể vượt qua những hạn chế của việc diễn giải dữ liệu từ tính truyền thống, lập bản đồ thành công các cấu trúc ở độ sâu 40 mét dưới đáy biển – những cấu trúc vốn đã “vô hình” với phương pháp acoustic suốt 18 năm.

Tác động của công nghệ này trải dài từ **oil & gas decommissioning**, **urban utility mapping**, **environmental protection** cho đến **marine operations**. Dù kết quả rất hứa hẹn, vẫn còn nhiều cơ hội phát triển, bao gồm **multi-physics integration**, xử lý dữ liệu **real-time**, và nâng cao khả năng phân giải.

Để hợp tác hoặc tìm hiểu thêm về việc triển khai, vui lòng liên hệ với chúng tôi qua email: [**santi@s2labs.co**](mailto:santi@s2labs.co) hoặc [**ryanqi@amazon.com**](mailto:ryanqi@amazon.com).

## **Thông tin về các tác giả**

<div style="display:flex; flex-direction:column; gap:1rem;">

<div style="display:flex; align-items:flex-start; gap:1rem;">
	<img src="/images/3-BlogsTranslated/3.2-Blog2/image5.png" alt="Santi Adavani" style="width:120px; height:120px; object-fit:cover; border-radius:8px;" />
	<div>
		<strong>Santi Adavani</strong><br/>
		Tiến sĩ Santi Adavani là người sáng lập và CEO của <strong>S2 Labs</strong>, một startup công nghệ chuyên sâu (deep tech) xây dựng các sản phẩm <strong>AI</strong> nhằm thúc đẩy khám phá khoa học. Trước <strong>S2 Labs</strong>, Santi là người sáng lập và CTO của <strong>RocketML</strong>, nơi ông đã xây dựng một nền tảng <strong>MLOps</strong> được hỗ trợ bởi <strong>HPC</strong> (Điện toán Hiệu năng Cao). Ông cũng từng là Trưởng bộ phận Sản phẩm và AI tại <strong>PostgresML</strong>, nơi ông lãnh đạo phát triển một cơ sở dữ liệu vector trong bộ nhớ dựa trên Postgres, và trước đó là Giám đốc Sản phẩm Cấp cao tại <strong>Intel</strong>. Santi có bằng <strong>Tiến sĩ</strong> về Khoa học và Kỹ thuật Tính toán từ <strong>Đại học Pennsylvania</strong>.
	</div>
</div>

<div style="display:flex; align-items:flex-start; gap:1rem;">
	<img src="/images/3-BlogsTranslated/3.2-Blog2/image6.png" alt="Jacques Guigné" style="width:120px; height:120px; object-fit:cover; border-radius:8px;" />
	<div>
		<strong>Jacques Guigné</strong><br/>
		Giáo sư Jacques Yves Guigné là Cố vấn Cấp cao cho <strong>Kraken Robotics</strong> ở Newfoundland, Canada. Ông giữ chức vụ Giám đốc Khoa học (CSO) của <strong>Subsea Micropiles Ltd.</strong>, công ty hoạt động tại Ireland và Vương quốc Anh. Ông cũng là Giám đốc Điều hành của <strong>Acoustic Zoom Inc.</strong>, một công ty nghiên cứu địa vật lý hàng đầu. Jacques mang đến kinh nghiệm phong phú về hình ảnh âm học và đã đóng góp đáng kể vào việc lập bản đồ đáy biển phức tạp. Những thành tựu khoa học của ông bao gồm hơn 80 bằng sáng chế và 70 ấn phẩm đã nhận được số lượng trích dẫn ấn tượng trên ResearchGate. Ông đã được vinh danh trong lĩnh vực vật lý với các <strong>Huy chương Deryck Chesterman và Rayleigh</strong>, phản ánh những đóng góp của ông cho địa vật lý, minh chứng bằng bằng <strong>DSc</strong> và <strong>Tiến sĩ</strong> của mình. Ngoài ra, ông còn được công nhận là <strong>Thành viên của Geoscience Canada</strong> và là Giám đốc của <strong>PEGNL</strong> (Kỹ sư Chuyên nghiệp và Nhà Khoa học Địa chất Newfoundland và Labrador).
	</div>
</div>

<div style="display:flex; align-items:flex-start; gap:1rem;">
	<img src="/images/3-BlogsTranslated/3.2-Blog2/image7.png" alt="Ryan Qi" style="width:120px; height:120px; object-fit:cover; border-radius:8px;" />
	<div>
		<strong>Ryan Qi</strong><br/>
		Ryan có 19 năm kinh nghiệm trong lĩnh vực mô hình hóa và mô phỏng <strong>Đa Vật lý (Multiphysics)</strong>, chiến lược và phát triển kinh doanh trên cả mảng công nghiệp và kỹ thuật số. Tại AWS, Ryan là <strong>Trưởng nhóm BD/GTM Toàn cầu Chính (Principal Worldwide BD/GTM Leader)</strong>, tập trung vào các công nghệ mô phỏng và hệ thống tự hành.
	</div>
</div>

<div style="display:flex; align-items:flex-start; gap:1rem;">
	<img src="/images/3-BlogsTranslated/3.2-Blog2/image8.png" alt="Souvik Mukherjee" style="width:120px; height:120px; object-fit:cover; border-radius:8px;" />
	<div>
		<strong>Souvik Mukherjee</strong><br/>
		Tiến sĩ Souvik Mukherjee là thành viên sáng lập của <strong>EmPact-AI</strong> và là Cố vấn Kỹ thuật Chính. Sự nghiệp hơn 15 năm của ông trải dài qua nhiều lĩnh vực trong ngành năng lượng và công nghệ với vai trò là một nhà địa vật lý, nhà khoa học dữ liệu và người dẫn dắt sản phẩm nổi tiếng. Ông đã được công nhận với nhiều giải thưởng uy tín trong ngành như <strong>giải thưởng Shell GameChanger (2015)</strong>, giải <strong>bài báo xuất sắc nhất và đổi mới URTeC 2019</strong>, cùng nhiều giải thưởng khác. Ông cũng được công nhận về khả năng quản lý, thực hiện và cung cấp thành công nhiều dự án có giá trị hàng triệu đô la, bao gồm việc thương mại hóa thành công công nghệ phân định vết nứt thủy lực có chống đỡ từng đoạt giải thưởng, <strong>QUANTUM</strong> cho <strong>Carbo Ceramics</strong>, và việc thực hiện <strong>Nghiên cứu Thăm dò Tiên phong Shell (Shell Frontier Exploration Study)</strong>, điều phối một đội ngũ gồm 15 chuyên gia kỹ thuật thuộc nhiều chuyên môn và phòng ban, vốn đã có tác động tích cực mạnh mẽ đến chiến lược mua lại hợp đồng thuê trị giá <strong>100 triệu đô la</strong> của Shell.
	</div>
</div>

<div style="display:flex; align-items:flex-start; gap:1rem;">
	<img src="/images/3-BlogsTranslated/3.2-Blog2/image9.png" alt="Srinivas Tadepalli" style="width:120px; height:120px; object-fit:cover; border-radius:8px;" />
	<div>
		<strong>Srinivas Tadepalli</strong><br/>
		Srinivas là <strong>trưởng bộ phận đưa HPC ra thị trường (go-to-market) toàn cầu tại AWS</strong>, chịu trách nhiệm xây dựng một chiến lược GTM toàn diện cho nhiều khối lượng công việc <strong>HPC</strong> và <strong>điện toán tăng tốc (Accelerated computing)</strong> cho cả khách hàng thương mại và công khu vực công. Trước đây, ông làm việc tại <strong>Dassault Systems</strong> và có bằng <strong>Tiến sĩ</strong> về kỹ thuật y sinh.
	</div>
</div>

<div style="display:flex; align-items:flex-start; gap:1rem;">
	<img src="/images/3-BlogsTranslated/3.2-Blog2/image10.png" alt="Vidyasagar Ananthan" style="width:120px; height:120px; object-fit:cover; border-radius:8px;" />
	<div>
		<strong>Vidyasagar Ananthan</strong><br/>
		Vidyasagar chuyên sâu về <strong>điện toán hiệu năng cao (high performance computing)</strong>, <strong>mô phỏng số (numerical simulations)</strong>, <strong>kỹ thuật tối ưu hóa</strong> và <strong>phát triển phần mềm</strong> trong cả môi trường công nghiệp và học thuật. Tại AWS, Vidyasagar là <strong>Kiến trúc sư Giải pháp Cấp cao (Senior Solutions Architect)</strong>, phát triển các mô hình dự đoán và công nghệ mô phỏng.
	</div>
</div>

</div>

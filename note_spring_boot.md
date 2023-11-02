- java bean: là các class có hàm khởi tạo không tham số được đặt là public, từ đó gọi các hàm không tham số tạo thành các object.Ngoài ra còn có các hàm getter, sette).
- spring bean: là các object được quản lý bởi spring. Bất cứ một object nào được khởi tạo, cấu hình từ "sping container" đều được dọc là "sping bean". Spring bean không nhất thiết phải là "java bean".

- "@Conponent" và "@Bean":
  + Nơi sử dụng:
    + "@Component" có thể sử dụng trên bất kỳ lớp Java nào và thường được sử dụng để đánh dấu các thành phần của ứng dụng.
    + "@Bean" thường được sử dụng trong các lớp cấu hình(annotated với "@confuguration") và chỉ có thể sử dụng reen phạm vi các phương thức.
  + Dễ sử dụng:
    + "@Component" dễ sử dụng, chỉ cần thêm annotation lên lớp và Spring sẽ tự đọng quét và đăng ký nó như một bean.
    + "@Bean" đòi hỏi phải viết mã tạo "Bean" và cấu hình "Bean" một các rõ ràng trong các phương thức.
  + Autowiring:
    + Cả "@Component" và "@Bean" đề hỗ trự tự động nối dây (autowiring) bằng cách sử dụng các phương thức khởi tạo (constructor), setter hoặc thuong (field) để dưa các phị thuộc (dependencies) vào bean.
  + Người tạo bean: 
    + Với "@Component" Spring Framework tự dộng tạo vào quẩn lý các bean dựa trên cấu hình vào quết các lớp có annotaion "@Component".
    + Với "@Bean" tự viết mã tạo bean và cấu hình bean.
  + Khuyến nghị sử dụng:
    + "@Component" thích hợp để tạo các bean tong ứng dụng của bạn và dễ sử dụng.
    + "@Bean" thường được sử dụng khi cần kiểm soát cụ thể hơn về việc tạo và cấu hình bean, đặc biệt là khi làm việc với các thư việ bên thứ 3.
  + Số lượng bean cho mỗi lớp:
    + "@Component" mặc định sử dụng kiểu Singleton vho bean, nhưng cũng có thể cấu hình chúng để sử dụng kiểu Prototupe nế cần.
    + "@Bean" cho phét tạo một hoặc nhiều kiểu bean theo ý muốn.

- Comparing Lazy Initialization vs Eager Initialization:
  + Thời gian khởi tạo:
    + Lazy: Bean được khởi tạo khi lần đầu sử dụng trong ứng dụng.
    + Eager: Bean được khởi tạo khi ứng dụng khởi động.
  + Giá trị mặc định:
    + Lazy: Không phải mặc định.
    + Eager: Mặc định nếu không có có "@Lazy".
  + Cách khởi tạo:
    + Lazy: "@Lazy" hoặc "@Lazy(value=true)".
    + Eager: "@Layzy(value=false" hoặc không có mặt của "@Lazy".
  + Sử dụng khuyến nghị:
    + Lazy: Hiếm khi sử dụng.
    + Eager: Sử dụng rất thường xuyên.
  + Xử lý lỗi khởi tạo:
    + Lazy: Lỗi sẽ dẫn đến các ngoại lệ chạy.
    + Eager: Lỗi sẽ ngăn ứng dụng khởi động.
  + Tiêu thụ bộ nhớ:
    + Lazy: Ít (cho đến khi bean được khởi tạo).
    + Eager: Tất cả các bean được khởi tạo khi khởi động ứng dụng.
  + Kịch bản khuyến nghị:
    + Lazy: Bean ít khi được sử dụng trong ứng dụng.
    + Eager: Hầu hết các bean được sử dụng trong ứng dụng.

- Prototype vs Singleton Bean Scope.
 + Số lượng thể hiện:
    + Prototype: Có thể có nhiều thể hiện trong Spring IOC Container.
    + Singleton: Chỉ có một thể hiện trong Spring IOC Container.
 + Bean:
    + Prototype: Thể hiện mới của bean được tạo mỗi khi bean được tham chiếu.
    + Singleton: Cùng một thể hiện của bean được tái sử dụng.
 + Giá trị mặc định:
    + Prototype: Không phải là giá trị mặc định.
    + Singleton: Mặc định (hoặc có thể không được đặt).
 + Mã mẫu:
    + Prototype: @Scope(value=ConfigurableBeanFactory.SCOPE_PROTOTYPE).
    + Singleton: @Scope(value=ConfigurableBeanFactory.SCOPE_SINGLETON) hoặc giá trị mặc định.
 + Sử dụng khuyến nghị:
    + Prototype: Hiếm khi sử dụng.
    + Singleton: Sử dụng rất thường xuyên.
 + Kịch bản khuyến nghị:
    + Prototype: Bean có trạng thái (stateful).
    + Singleton: Bean không có trạng thái (stateless).

- So sánh Sử dụng Chú thích(Annotations) và Cấu hình XML(XML Configuration) trong Spring:
 + Dễ sử dụng:
    + Annotations: Rất dễ sử dụng (được định nghĩa gần nguồn - lớp, phương thức và/hoặc biến).
    + XML: Gặp khó khăn. 
 + Ngắn và gọn:
    + Annotations: .
    + XML: .
 + POJOs Sạch sẽ:
    + Annotations: Không. POJOs bị rối bởi các Chú thích Spring.
    + XML: Có. Không có thay đổi trong mã Java.
 + Dễ bảo trì:
    + Annotations:	Có.
    + XML: Không.
 + Tần suất sử dụng:
    + Annotations: Gần như tất cả các dự án gần đây.
    + XML: Hiếm khi.
 + Khuyến nghị:
    + Annotations: Cả hai đều được, NHƯNG hãy duy trì tính nhất quán.
    + XML: Đừng kết hợp cả hai.
 + Độ khó khi gỡ lỗi:
    + Annotations: Khó.
    + XML: Trung bình.

- Một số chú thích quan trọng trong Spring Framework:
  + @Configuration:
    + Chỉ ra rằng một lớp khải báo một hoặc nhiều phương thức "@Bean".
    + Có thể được xử lý bởi Spring container để tạo ra các định nghĩa bean.
    + Sử dụng trong cấu hình dựa trên Java để định nghĩa các bean và các phụ thuộc của chúng.
  + @ConponentScan:
    + Xác định các gói cụ thể để quét các thành phần Spring.
    + Nếu không xác định các gói cụ thể, quét sẽ diễn ra từ gói chứa lớp khai báo chú thích này.
    + Cho phép phát hiện tự động và đăng ký các bean được quản lý bởi Spring.
  + @Bean:
    + Chỉ ra rằng một phương thức tạo ra một bean được quản lý bởi Spring container.
    + Sử dụng trong các lớp "@Configuration" để định nghĩa và cấu hình các bean một cách tường minh.
    + Cung cấp sự kiểm soát tùy chỉnh về việc tạo và khởi tạo bean.
  + @Component:
    + Đánh dấu một lớp được chú thích là một "component" trong ngữ cảnh ứng dụng Spring.
    + Các lớp này được tự động phát hiện trong quá trình quét thành phần và có thể đăng ký như các bean.
  + @Service:
    + Một loại hình đặc biệt của @Component cho biết một lớp được chú thích chứa logic kinh doanh.
    + Thường được sử dụng cho các lớp dịch vụ (service), thường nằm trong lớp logic kinh doanh của ứng dụng.
  + @Controller:
    + Một loại hình đặc biệt của @Component cho biết một lớp được chú thích là "Controller."
    + Sử dụng trong ứng dụng web và phát triển REST API để định nghĩa logic xử lý yêu cầu.
  + @Repository:
    + Một loại hình đặc biệt của @Component cho biết một lớp được chú thích được sử dụng để truy xuất và điều khiển dữ liệu trong cơ sở dữ liệu.
    + Thường được sử dụng cho đối tượng truy cập dữ liệu (DAO) trong các ứng dụng Spring.
  + @Primary:
    + Chỉ ra rằng một bean nên được ưu tiên khi có nhiều ứng viên đủ điều kiện để tự động nối dây một phụ thuộc có một giá trị duy nhất.
    + Thường được sử dụng để chỉ định bean chính để được tiêm khi có nhiều bean cùng kiểu có sẵn để tự động nối dây.
  + @Qualifier:
    + Sử dụng trên trường hoặc tham số để xác định một điểm đánh dấu cho các bean ứng cử khi tự động nối dây.
    + Thường được sử dụng kết hợp với @Autowired để làm sáng tỏ rằng bean nào nên được tiêm khi có nhiều bean cùng kiểu.
  + @Lazy:
    + Chỉ ra rằng một bean nên được khởi tạo lười biếng.
    + Sự vắng mặt của chú thích @Lazy sẽ dẫn đến khởi tạo nhanh chóng (eager initialization), trong đó bean được tạo khi ngữ cảnh ứng dụng khởi động. Với @Lazy, bean chỉ được khởi tạo khi bạn lần đầu tiên sử dụng nó.
  + @Scope:
    + Định nghĩa phạm vi của một bean.
    + @Scope(value=ConfigurableBeanFactory.SCOPE_PROTOTYPE) chỉ định rằng bean thuộc phạm vi prototype, có nghĩa là một thể hiện mới sẽ được tạo ra mỗi khi bạn tham chiếu đến bean đó.
    + Phạm vi mặc định là singleton, có nghĩa là chỉ có một thể hiện trong mỗi ngữ cảnh IOC của Spring.
  + @PostConstruct:
    + Xác định phương thức sẽ được thực thi sau khi việc tiêm phụ thuộc đã hoàn tất để thực hiện bất kỳ khởi tạo nào.
    + Thông thường được sử dụng để thực hiện các công việc chuẩn bị sau khi bean được khởi tạo, chẳng hạn như cấu hình.
  + @PreDestroy:
    + Xác định phương thức sẽ nhận thông báo gọi lại để báo hiệu rằng thể hiện đang trong quá trình bị loại bỏ bởi container.
    + Thường được sử dụng để giải phóng tài nguyên mà thể hiện đang giữ.
  + @Named:
    + Annotation Jakarta CDI tương tự với @Component trong Spring.
    + Được sử dụng để đánh dấu một lớp là một thành phần CDI và cho phép nó được quản lý bởi CDI container.
  + @Inject:
    + Annotation Jakarta CDI tương tự với @Autowired trong Spring.
    + Sử dụng để tự động nối dây (autowire) các phụ thuộc của một bean Jakarta CDI.

- Quick Review of Important Spring Concepts:
  + Dependency Injection (DI): 
    + Xác định các bean, phụ thuộc của chúng và kết nối chúng với nhau.
    + Cung cấp Inversion of Control (IOC) bằng cách quản lý việc tạo và quản lý các đối tượng.
  + Constructor Injection (Tiêm phụ thuộc thông qua hàm tạo):
    + Các phụ thuộc được thiết lập bằng cách tạo Bean bằng hàm tạo của nó.
  + Setter Injection (Tiêm phụ thuộc thông qua phương thức thiết lập):
    + Các phụ thuộc được thiết lập bằng cách gọi các phương thức thiết lập (setter) trên các Bean.
  + Field Injection (Tiêm phụ thuộc thông qua trường):
    + Không sử dụng setter hoặc hàm tạo. Phụ thuộc được tiêm vào bằng cách sử dụng kỹ thuật phản ánh (reflection).
  + IOC Container (IOC Container của Spring):
    + Ngữ cảnh Spring quản lý các Bean Spring và chu kỳ sống của chúng.
  + Bean Factory (Nhà máy Bean cơ bản của Spring):
    + Container IOC cơ bản của Spring, quản lý các đối tượng Bean và cung cấp khả năng quản lý Bean cơ bản.
  + Application Context (Ngữ cảnh ứng dụng của Spring):
    + Container IOC nâng cao của Spring với các tính năng dành cho doanh nghiệp.
    + Dễ sử dụng trong các ứng dụng web và tích hợp tốt với Spring AOP (Aspect-Oriented Programming).
  + Spring Beans (Bean của Spring):
    + Các đối tượng được quản lý bởi Spring, có thể là các lớp hoặc đối tượng được quản lý bởi Spring IOC Container.

- @Controller:
  + Chú thích @Controller được sử dụng để đánh dấu một lớp Java là một Spring MVC controller.
  + Controllers trong Spring MVC chịu trách nhiệm xử lý yêu cầu HTTP, tương tác với model (dữ liệu), và trả về các view (giao diện người dùng) để hiển thị kết quả.
  + Controllers thường được sử dụng cho các ứng dụng web truyền thống.
- @RestController:
  + Chú thích @RestController là một sự chuyên biệt của @Controller và thường được sử dụng cho việc xây dựng RESTful web services.
  + Nó kết hợp chú thích @Controller và @ResponseBody, tức là nó tự động chuyển đổi các giá trị trả về từ các phương thức controller thành định dạng JSON hoặc XML phù hợp cho API REST.
- @RequestMapping():
  + Chú thích @RequestMapping() được sử dụng để ánh xạ một phương thức trong controller với một URI hoặc URL cụ thể.
  + Nó xác định URL mà phương thức sẽ xử lý khi một yêu cầu HTTP đến.
- Request Methods for REST API
  + GET - Retrieve details of a resource (Truy xuất chi tiết của một tài nguyên: Sử dụng để lấy thông tin chi tiết về một tài nguyên cụ thể từ máy chủ, thường là thông qua URL. Không làm thay đổi dữ liệu trên máy chủ).
  + POST - Create a new resource (Tạo một tài nguyên mới: Sử dụng để tạo một tài nguyên mới trên máy chủ. Thông qua phương thức này, dữ liệu mới được gửi đến máy chủ để tạo một tài nguyên mới)
  + PUT - Update an existing resource ( Cập nhật một tài nguyên hiện có: Sử dụng để cập nhật toàn bộ thông tin của một tài nguyên đã tồn tại hoặc tạo tài nguyên mới nếu chưa tồn tại.)
  + PATCH - Update part of a resource (Cập nhật một phần của tài nguyên: Sử dụng để cập nhật một phần nhỏ của tài nguyên đã tồn tại mà không ảnh hưởng đến các phần khác của tài nguyên)
  + DELETE - Delete a resource(Xóa một tài nguyên: Sử dụng để xóa hoặc loại bỏ một tài nguyên cụ thể từ máy chủ)

- Important Response Statuses:
  + 400: loi xac thuc (validable error)
  + 200: thanh cong (success)
  + 201: tao thanh cong (created)
  + 204: khong cung cap noi dung (No content)
  + 401: unauthorized  (when authorization fails) -Mã trạng thái 401 được sử dụng khi yêu cầu HTTP yêu cầu xác thực (authentication) nhưng xác thực không thành công hoặc chưa được thực hiện.
  + 400: yeu cau khong hop le-vi du: loi xac thuc (bad Request) - Mã trạng thái 400 được sử dụng khi máy chủ không thể hiểu hoặc xử lý yêu cầu HTTP do yêu cầu không hợp lệ hoặc không đúng định dạng.
  + 404: khong tim thay tai nguyen (resource is not found)
  + 500: loi ngoai le tu may chu (Server error)

- Versioning REST API - Options 
  + URI Versioning - Twitter
    + http://localhost:8080/v1/person
    + http://localhost:8080/v2/person
  + Request Parameter versioning - Amazon
    + http://localhost:8080/person?version=1
    + http://localhost:8080/person?version=2
  + (Custom) headers versioning - Microsoft
    + SAME-URL headers=[X-API-VERSION=1]
    + SAME-URL headers=[X-API-VERSION=2]
  + Media type versioning (a.k.a “content negotiation” or “accept header”) - GitHub
    + SAME-URL produces=application/vnd.company.app-v1+json
    + SAME-URL produces=application/vnd.company.app-v2+json

- Customizing REST API Responses - Filtering and more..
  + Two types:
    + Static Filtering: Same filtering for a bean across different REST API
      + @JsonIgnoreProperties, @JsonIgnore
        @JsonIgnoreProperties(value = {"fieldToIgnore1", "fieldToIgnore2"})
        public class MyBean {
          private String field1;
          private String field2;
          
          @JsonIgnore
          private String fieldToIgnore1;
          
          // Getter và Setter
        }
    + Dynamic Filtering: Customize filtering for a bean for specific REST API
      + @JsonFilter with FilterProvider
          @JsonFilter("myDynamicFilter")
          public class MyBean {
              private String field1;
              private String field2;
              private String fieldToInclude;
          }
          @RestController
          public class MyController {
              @GetMapping("/filtered-data")
              public MappingJacksonValue retrieveFilteredData() {
                  MyBean myBean = new MyBean();
                  // Set các giá trị cho myBean
                  
                  SimpleBeanPropertyFilter filter = SimpleBeanPropertyFilter.filterOutAllExcept("field1", "field2");
                  FilterProvider filters = new SimpleFilterProvider().addFilter("myDynamicFilter", filter);
                  
                  MappingJacksonValue mapping = new MappingJacksonValue(myBean);
                  mapping.setFilters(filters);
                  
                  return mapping;
              }
          }



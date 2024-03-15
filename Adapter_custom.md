| Kiểu Adapter          | Ưu điểm                                                                                                                                                                                                                                    | Nhược điểm                                                                                                                                                                                                                          |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ArrayAdapter          | - Dễ sử dụng và triển khai. - Phù hợp cho các danh sách dữ liệu đơn giản.                                                                                                                                                                 | - Hạn chế trong việc tùy chỉnh giao diện của mỗi mục trong danh sách. - Không linh hoạt khi muốn hiển thị dữ liệu phức tạp hơn, ví dụ: hiển thị hình ảnh hoặc dữ liệu từ nguồn dữ liệu không phải là mảng.                 |
| BaseAdapter           | - Linh hoạt và có thể tùy chỉnh hoàn toàn theo yêu cầu của ứng dụng. - Cho phép bạn tạo các giao diện phức tạp hơn cho mỗi mục trong danh sách. - Có thể kết hợp với nhiều loại dữ liệu khác nhau.                                    | - Cần phải triển khai nhiều phương thức của lớp trừu tượng BaseAdapter, làm tăng độ phức tạp của mã nguồn. - Yêu cầu có kiến thức sâu về cách hoạt động của Adapter và ListView/RecyclerView.                                      |
| RecyclerView.Adapter | - Hiệu suất cao hơn so với ListView và hỗ trợ cho các giao diện danh sách phức tạp. - Cung cấp kiểm soát linh hoạt hơn về cách dữ liệu được hiển thị và quản lý trong RecyclerView. - Hỗ trợ cho nhiều loại bố cục khác nhau. | - Yêu cầu kiến thức sâu về RecyclerView và ViewHolder để triển khai một cách hiệu quả. - Cần phải triển khai nhiều phương thức và các lớp bổ sung để đáp ứng yêu cầu cụ thể của ứng dụng.                                       |
| CursorAdapter         | - Tự động cập nhật dữ liệu từ con trỏ (cursor) của cơ sở dữ liệu. - Hiệu suất tốt với cơ sở dữ liệu SQLite và ListView.                                                                                                             | - Hạn chế trong việc tùy chỉnh giao diện của mỗi mục trong danh sách. - Không thích hợp cho các tác vụ hiển thị dữ liệu từ nguồn dữ liệu không phải là cơ sở dữ liệu SQLite hoặc khi cần hiển thị dữ liệu phức tạp hơn. |
| PagerAdapter          | - Cho phép hiển thị nhiều màn hình hoặc trang dữ liệu trong một ViewPager. - Linh hoạt và có thể tùy chỉnh giao diện của mỗi trang.                                                                                                 | - Yêu cầu kiến thức về ViewPager và các lớp con của PagerAdapter như FragmentPagerAdapter hoặc FragmentStatePagerAdapter. - Không thích hợp cho các giao diện danh sách tĩnh hoặc hiển thị dữ liệu từ nguồn không phải là Fragment. |
| SimpleAdapter         | - Dễ sử dụng và triển khai. - Phù hợp cho các danh sách dữ liệu đơn giản và yêu cầu giao diện đơn giản.                                                                                                                                | - Hạn chế trong việc tùy chỉnh giao diện của mỗi mục trong danh sách. - Không linh hoạt khi muốn hiển thị dữ liệu phức tạp hơn, ví dụ: hiển thị hình ảnh hoặc dữ liệu từ nguồn dữ liệu không phải là mảng.                 |
| Wrapper Adapter       | - Cho phép mở rộng hoặc thay đổi hành vi của Adapter gốc mà không cần thay đổi mã nguồn của Adapter đó.                                                                                                                              | - Yêu cầu hiểu biết sâu về cách hoạt động của Adapter gốc và các phương thức của nó. - Không thích hợp cho các tình huống cần tạo ra một Adapter hoàn toàn mới với giao diện và hành vi hoàn toàn khác biệt.               |

# Custom ArrayAdapter Example

### Product Class

```java
public class Product {
    private String name;
    private double price;
    private int imageResourceId;

    public Product(String name, double price, int imageResourceId) {
        this.name = name;
        this.price = price;
        this.imageResourceId = imageResourceId;
    }

    public String getName() {
        return name;
    }

    public double getPrice() {
        return price;
    }

    public int getImageResourceId() {
        return imageResourceId;
    }
}
```
### ProductAdapter Class

```java
import android.content.Context;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.ArrayAdapter;
import android.widget.ImageView;
import android.widget.TextView;

import java.util.ArrayList;

public class ProductAdapter extends ArrayAdapter<Product> {

    public ProductAdapter(Context context, ArrayList<Product> products) {
        super(context, 0, products);
    }

    @Override
    public View getView(int position, View convertView, ViewGroup parent) {
        // Get the data item for this position
        Product product = getItem(position);

        // Check if an existing view is being reused, otherwise inflate the view
        if (convertView == null) {
            convertView = LayoutInflater.from(getContext()).inflate(R.layout.item_product, parent, false);
        }

        // Lookup view for data population
        TextView productName = convertView.findViewById(R.id.product_name);
        TextView productPrice = convertView.findViewById(R.id.product_price);
        ImageView productImage = convertView.findViewById(R.id.product_image);

        // Populate the data into the template view using the data object
        productName.setText(product.getName());
        productPrice.setText(String.valueOf(product.getPrice()));
        productImage.setImageResource(product.getImageResourceId());

        // Return the completed view to render on screen
        return convertView;
    }
}

```
### item_product.xml

```xml
<!-- item_product.xml -->
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:orientation="horizontal">

    <ImageView
        android:id="@+id/product_image"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical">

        <TextView
            android:id="@+id/product_name"
            android:layout_width="match_parent"
            android:layout_height="wrap_content" />

        <TextView
            android:id="@+id/product_price"
            android:layout_width="match_parent"
            android:layout_height="wrap_content" />
    </LinearLayout>

</LinearLayout>
```
### MainActivity class

```java
import android.os.Bundle;
import android.widget.ListView;

import androidx.appcompat.app.AppCompatActivity;

import java.util.ArrayList;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        ArrayList<Product> products = new ArrayList<>();
        products.add(new Product("Product 1", 10.99, R.drawable.product1));
        products.add(new Product("Product 2", 15.99, R.drawable.product2));
        // Add more products as needed

        ProductAdapter adapter = new ProductAdapter(this, products);
        ListView listView = findViewById(R.id.listView);
        listView.setAdapter(adapter);
    }
}
```

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

### ArrayAdapter Class

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

### BaseAdapter class

```java
import android.content.Context;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.BaseAdapter;
import android.widget.ImageView;
import android.widget.TextView;

import java.util.ArrayList;

public class ProductAdapter extends BaseAdapter {

    private Context mContext;
    private ArrayList<Product> mProductList;

    public ProductAdapter(Context context, ArrayList<Product> productList) {
        mContext = context;
        mProductList = productList;
    }

    @Override
    public int getCount() {
        return mProductList.size();
    }

    @Override
    public Object getItem(int position) {
        return mProductList.get(position);
    }

    @Override
    public long getItemId(int position) {
        return position;
    }

    @Override
    public View getView(int position, View convertView, ViewGroup parent) {
        ViewHolder holder;

        if (convertView == null) {
            convertView = LayoutInflater.from(mContext).inflate(R.layout.list_item_product, parent, false);
            holder = new ViewHolder();
            holder.nameTextView = convertView.findViewById(R.id.product_name);
            holder.priceTextView = convertView.findViewById(R.id.product_price);
            holder.imageView = convertView.findViewById(R.id.product_image);
            convertView.setTag(holder);
        } else {
            holder = (ViewHolder) convertView.getTag();
        }

        Product product = (Product) getItem(position);

        holder.nameTextView.setText(product.getName());
        holder.priceTextView.setText(String.valueOf(product.getPrice()));
        holder.imageView.setImageResource(product.getImageResourceId());

        return convertView;
    }

    private static class ViewHolder {
        TextView nameTextView;
        TextView priceTextView;
        ImageView imageView;
    }
}
```
### RecyclerView.Adapter class

```java
import android.content.Context;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.ImageView;
import android.widget.TextView;

import androidx.annotation.NonNull;
import androidx.recyclerview.widget.RecyclerView;

import java.util.List;

public class ProductAdapter extends RecyclerView.Adapter<ProductAdapter.ProductViewHolder> {

    private Context context;
    private List<Product> productList;

    public ProductAdapter(Context context, List<Product> productList) {
        this.context = context;
        this.productList = productList;
    }

    @NonNull
    @Override
    public ProductViewHolder onCreateViewHolder(@NonNull ViewGroup parent, int viewType) {
        View view = LayoutInflater.from(context).inflate(R.layout.item_product, parent, false);
        return new ProductViewHolder(view);
    }

    @Override
    public void onBindViewHolder(@NonNull ProductViewHolder holder, int position) {
        Product product = productList.get(position);
        holder.txtName.setText(product.getName());
        holder.txtPrice.setText(String.valueOf(product.getPrice()));
        holder.imgProduct.setImageResource(product.getImageResourceId());
    }

    @Override
    public int getItemCount() {
        return productList.size();
    }

    public static class ProductViewHolder extends RecyclerView.ViewHolder {
        TextView txtName, txtPrice;
        ImageView imgProduct;

        public ProductViewHolder(@NonNull View itemView) {
            super(itemView);
            txtName = itemView.findViewById(R.id.txt_name);
            txtPrice = itemView.findViewById(R.id.txt_price);
            imgProduct = itemView.findViewById(R.id.img_product);
        }
    }
}
```
### CursorAdapter class

```java
import android.content.Context;
import android.database.Cursor;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.CursorAdapter;
import android.widget.ImageView;
import android.widget.TextView;

public class ProductAdapter extends CursorAdapter {

    public ProductAdapter(Context context, Cursor cursor) {
        super(context, cursor, 0);
    }

    @Override
    public View newView(Context context, Cursor cursor, ViewGroup parent) {
        return LayoutInflater.from(context).inflate(R.layout.product_item, parent, false);
    }

    @Override
    public void bindView(View view, Context context, Cursor cursor) {
        // Mapping data from cursor to views
        TextView nameTextView = view.findViewById(R.id.name);
        TextView priceTextView = view.findViewById(R.id.price);
        ImageView imageView = view.findViewById(R.id.image);

        // Extracting data from cursor
        String name = cursor.getString(cursor.getColumnIndexOrThrow("name"));
        double price = cursor.getDouble(cursor.getColumnIndexOrThrow("price"));
        int imageResourceId = cursor.getInt(cursor.getColumnIndexOrThrow("imageResourceId"));

        // Setting data to views
        nameTextView.setText(name);
        priceTextView.setText(String.valueOf(price));
        imageView.setImageResource(imageResourceId);
    }
}
```
### PagerAdapter class

```java
import android.content.Context;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.ImageView;
import android.widget.TextView;

import androidx.annotation.NonNull;
import androidx.viewpager.widget.PagerAdapter;

import java.util.List;

public class ProductPagerAdapter extends PagerAdapter {

    private Context mContext;
    private List<Product> mProductList;

    public ProductPagerAdapter(Context context, List<Product> productList) {
        mContext = context;
        mProductList = productList;
    }

    @Override
    public int getCount() {
        return mProductList.size();
    }

    @Override
    public boolean isViewFromObject(@NonNull View view, @NonNull Object object) {
        return view == object;
    }

    @NonNull
    @Override
    public Object instantiateItem(@NonNull ViewGroup container, int position) {
        LayoutInflater inflater = LayoutInflater.from(mContext);
        View itemView = inflater.inflate(R.layout.item_product, container, false);

        // Binding data
        ImageView imageView = itemView.findViewById(R.id.imageViewProduct);
        TextView nameTextView = itemView.findViewById(R.id.textViewProductName);
        TextView priceTextView = itemView.findViewById(R.id.textViewProductPrice);

        Product product = mProductList.get(position);
        imageView.setImageResource(product.getImageResourceId());
        nameTextView.setText(product.getName());
        priceTextView.setText(String.valueOf(product.getPrice()));

        container.addView(itemView);

        return itemView;
    }

    @Override
    public void destroyItem(@NonNull ViewGroup container, int position, @NonNull Object object) {
        container.removeView((View) object);
    }
}
```
### SimpleAdapter class

```java
import android.content.Context;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.ImageView;
import android.widget.SimpleAdapter;
import android.widget.TextView;

import java.util.List;
import java.util.Map;

public class ProductAdapter extends SimpleAdapter {
    private Context mContext;
    private List<? extends Map<String, ?>> mData;
    private int mResource;
    private String[] mFrom;
    private int[] mTo;

    public ProductAdapter(Context context, List<? extends Map<String, ?>> data, int resource, String[] from, int[] to) {
        super(context, data, resource, from, to);
        this.mContext = context;
        this.mData = data;
        this.mResource = resource;
        this.mFrom = from;
        this.mTo = to;
    }

    @Override
    public View getView(int position, View convertView, ViewGroup parent) {
        View view = convertView;
        ViewHolder holder;

        if (view == null) {
            LayoutInflater inflater = (LayoutInflater) mContext.getSystemService(Context.LAYOUT_INFLATER_SERVICE);
            view = inflater.inflate(mResource, null);
            holder = new ViewHolder();
            holder.nameTextView = (TextView) view.findViewById(R.id.product_name);
            holder.priceTextView = (TextView) view.findViewById(R.id.product_price);
            holder.imageView = (ImageView) view.findViewById(R.id.product_image);
            view.setTag(holder);
        } else {
            holder = (ViewHolder) view.getTag();
        }

        Map<String, ?> item = mData.get(position);
        if (item != null) {
            holder.nameTextView.setText((String) item.get("name"));
            holder.priceTextView.setText(String.valueOf(item.get("price")));
            holder.imageView.setImageResource((Integer) item.get("imageResourceId"));
        }

        return view;
    }

    static class ViewHolder {
        TextView nameTextView;
        TextView priceTextView;
        ImageView imageView;
    }
}
```
### Wrapper Adapter class

```java
import android.content.Context;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.BaseAdapter;
import android.widget.ImageView;
import android.widget.TextView;
import java.util.List;

public class ProductAdapter extends BaseAdapter {
    private Context mContext;
    private List<Product> mProductList;

    public ProductAdapter(Context context, List<Product> productList) {
        mContext = context;
        mProductList = productList;
    }

    @Override
    public int getCount() {
        return mProductList.size();
    }

    @Override
    public Object getItem(int position) {
        return mProductList.get(position);
    }

    @Override
    public long getItemId(int position) {
        return position;
    }

    @Override
    public View getView(int position, View convertView, ViewGroup parent) {
        ViewHolder viewHolder;

        if (convertView == null) {
            convertView = LayoutInflater.from(mContext).inflate(R.layout.item_product, parent, false);
            viewHolder = new ViewHolder();
            viewHolder.nameTextView = convertView.findViewById(R.id.nameTextView);
            viewHolder.priceTextView = convertView.findViewById(R.id.priceTextView);
            viewHolder.imageView = convertView.findViewById(R.id.imageView);
            convertView.setTag(viewHolder);
        } else {
            viewHolder = (ViewHolder) convertView.getTag();
        }

        Product product = (Product) getItem(position);
        viewHolder.nameTextView.setText(product.getName());
        viewHolder.priceTextView.setText(String.valueOf(product.getPrice()));
        viewHolder.imageView.setImageResource(product.getImageResourceId());

        return convertView;
    }

    private static class ViewHolder {
        TextView nameTextView;
        TextView priceTextView;
        ImageView imageView;
    }
}
```

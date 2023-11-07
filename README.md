# Tugas UTS 
Repository ini dibuat untuk memenuhi tugas UTS - Pemrograman Mobile.

Nama : Aditya Achya Ananta Nur

NIM : 312210714

Kelas : TI.22.B1

Mata Kuliah : Pemrograman Mobile

Dosen : Donny Maulana

# Toast Fibonacci App

1. Berikut untuk Source Code Toast Fibonacci App

  activity_main.Xml (dibuat dengan design pada android studio):

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context="com.androidstudiobos.twoactivities.MainActivity">

    <Button
        android:id="@+id/button_toast"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="@color/colorPrimary"
        android:text="@string/btn_label_toast"
        android:onClick="showToast"
        android:textColor="@android:color/white"
        tools:ignore="OnClick"
        android:layout_marginLeft="6dp"
        android:layout_marginTop="6dp"
        android:layout_marginRight="6dp"/>

    <TextView
        android:id="@+id/show_count"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_weight="2"
        android:gravity="center"
        android:text="@string/count_initial_value"
        android:textColor="@color/colorPrimary"
        android:textSize="@dimen/count_text_size"
        android:background="@color/myBackgroundColor"
        android:textStyle="bold"
        android:layout_marginLeft="6dp"
        android:layout_marginTop="6dp"
        android:layout_marginRight="6dp"/>

    <Button
        android:id="@+id/button_count"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:onClick="countUp"
        android:background="@color/colorPrimary"
        android:layout_marginBottom="6dp"
        android:layout_marginLeft="6dp"
        android:layout_marginTop="6dp"
        android:layout_marginRight="6dp"
        android:text="@string/btn_label_count"
        android:textColor="@android:color/white"
        tools:ignore="OnClick" />
</LinearLayout>
```

Penjelasan :

Button pertama berisi tulisan Toast berfungsi agar pengguna tau bahwa aplikasi yang digunakan yaitu aplikasi TOAST

Yang kedua TEXT VIEW yang menampilkan hasil hitungan Fibonacci sesuai dengan beberapa kali kita pencet button ketiga yaitu button COUNT


MainActivity.Java :

'''

    private Context context;
    private int mCount = 0;
    private TextView mShowCount;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        mShowCount = (TextView) findViewById(R.id.show_count);
    }


    private int fibonacci( int n){

        if (n <= 1) {
            return n;
        } else {
            int fib1 = 0;
            int fib2 = 1;
            int result = 0;

            for (int i = 2; i <= n; i++) {
                result = fib1 + fib2;
                fib1 = fib2;
                fib2 = result;
            }

            return result;
        }
    }
    public void showToast(View view) {
        String myString = "Hallo toast";
        Toast toast = Toast.makeText(getApplicationContext(), myString, Toast.LENGTH_LONG);
        toast.show();
    }

    public void countUp(View view) {
        int fibonacciValue = fibonacci(mCount);

        if (mShowCount != null) {
            mShowCount.setText(Integer.toString(fibonacciValue));

            if (fibonacciValue % 2 == 0) {
                mShowCount.setTextColor(getResources().getColor(R.color.evenColor));
            } else {
                mShowCount.setTextColor(getResources().getColor(R.color.oddColor));
            }
        }
        mCount++;
    }
    
'''

Penjelasan
pada Source Code 

    if (n <= 1) {

            return n;
        } else {
            int fib1 = 0;
            int fib2 = 1;
            int result = 0;

            for (int i = 2; i <= n; i++) {
                result = fib1 + fib2;
                fib1 = fib2;
                fib2 = result;
            }

digunakan untuk memanggil hasil hitungan fibonacci

selain 2 code diatas terdapat beberapa code yang saya buat contohnya ada di values seperti berikut

Color

'''

    <resources>
          <color name="black">#FF000000</color>
          <color name="white">#FFFFFFFF</color>
          <color name="activityBackground">#FFFFFFFF</color>
          <color name="colorPrimary">#01034f</color>
          <color name="colorPrimaryDark">#303F9F</color>
          <color name="colorAccent">#FF4081</color>
          <color name="myBackgroundColor">#FFF043</color>
          <color name="evenColor">#00FFFF</color> <!-- Warna aqua untuk angka genap -->
          <color name="oddColor">#076101</color>  <!-- Warna hijau untuk angka ganjil -->
    </resources>

'''

dimens
'''

    <resources>
        <dimen name="activity_horizontal_margin">16dp</dimen>
        <dimen name="activity_vertical_margin">16dp</dimen>
        <dimen name="count_text_size">160dp</dimen>
    </resources>

'''


1.Create custom_edittext.xml

    Right-click on the drawable folder under the res folder then click on New -> Drawable Resource File
    
    The round corners are 20dp, you can customize them as per your requirements.
    
    Type the below code:
    
    <?xml version="1.0" encoding="utf-8"?>
    <shape xmlns:android="http://schemas.android.com/apk/res/android"
        android:shape="rectangle">
        <stroke
            android:width="3dp"
            android:color="@color/purple"/>
        <corners
            android:radius="20dp"/>
    </shape>

  --------
  
2. Type the below code in activity_main.xml

      We have created a minimal and beautiful design for the login page in android studio.
      
      We have used Linear Layout in which a CardView is present and then further two EditText and one Button.
      
      To give it a style, we have added the CardView background as custom_edittext.xml which will provide round corners with purple color.
      
      <?xml version="1.0" encoding="utf-8"?>
      <LinearLayout
          xmlns:android="http://schemas.android.com/apk/res/android"
          xmlns:app="http://schemas.android.com/apk/res-auto"
          xmlns:tools="http://schemas.android.com/tools"
          xmlns:card_view="http://schemas.android.com/apk/res-auto"
          android:layout_width="match_parent"
          android:layout_height="match_parent"
          android:orientation="vertical"
          android:gravity="center"
          android:background="@drawable/loginbkg"
          tools:context=".MainActivity">
          <androidx.cardview.widget.CardView
              android:layout_width="match_parent"
              android:layout_height="wrap_content"
              android:layout_margin="30dp"
              app:cardCornerRadius="30dp"
              app:cardElevation="20dp"
              android:background="@drawable/custom_edittext">
              <LinearLayout
                  android:layout_width="match_parent"
                  android:layout_height="wrap_content"
                  android:orientation="vertical"
                  android:layout_gravity="center_horizontal"
                  android:padding="24dp">
                  <TextView
                      android:layout_width="match_parent"
                      android:layout_height="wrap_content"
                      android:text="Login"
                      android:id="@+id/loginText"
                      android:textSize="36sp"
                      android:textAlignment="center"
                      android:textStyle="bold"
                      android:textColor="@color/purple"/>
                  <EditText
                      android:layout_width="match_parent"
                      android:layout_height="50dp"
                      android:id="@+id/username"
                      android:background="@drawable/custom_edittext"
                      android:drawableLeft="@drawable/ic_baseline_person_24"
                      android:drawablePadding="8dp"
                      android:hint="Username"
                      android:padding="8dp"
                      android:textColor="@color/black"
                      android:textColorHighlight="@color/cardview_dark_background"
                      android:layout_marginTop="40dp"/>
                  <EditText
                      android:layout_width="match_parent"
                      android:layout_height="50dp"
                      android:id="@+id/password"
                      android:background="@drawable/custom_edittext"
                      android:drawableLeft="@drawable/ic_baseline_lock_24"
                      android:drawablePadding="8dp"
                      android:hint="Password"
                      android:padding="8dp"
                      android:inputType="textPassword"
                      android:textColor="@color/black"
                      android:textColorHighlight="@color/cardview_dark_background"
                      android:layout_marginTop="20dp"/>
                  <Button
                      android:layout_width="match_parent"
                      android:layout_height="60dp"
                      android:id="@+id/loginButton"
                      android:text="Login"
                      android:textSize="18sp"
                      android:layout_marginTop="30dp"
                      android:backgroundTint="@color/purple"
                      app:cornerRadius = "20dp"/>
              </LinearLayout>
          </androidx.cardview.widget.CardView>
          <TextView
              android:layout_width="wrap_content"
              android:layout_height="wrap_content"
              android:padding="8dp"
              android:text="Not yet registered? SignUp Now"
              android:textSize="14sp"
              android:textAlignment="center"
              android:id="@+id/signupText"
              android:textColor="@color/purple"
              android:layout_marginBottom="20dp"/>
      </LinearLayout>

  --------

Step 5: Type the below code in MainActivity.java

There is a button named as loginButton on which we have set an onClickListener and in that, we have written the below logic.

We have set the username as “user” and the password as “1234”, so if the string matches with the user’s string then the toast will be shown as Login Successful but if the user’s string does not match with the static string then the toast will be shown as “Login Failed!”.

    package com.example.loginscreen;
    import androidx.appcompat.app.AppCompatActivity;
    import android.os.Bundle;
    import android.view.View;
    import android.widget.Button;
    import android.widget.EditText;
    import android.widget.Toast;
    public class MainActivity extends AppCompatActivity {
        EditText username;
        EditText password;
        Button loginButton;
        @Override
        protected void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.activity_main);
            username = findViewById(R.id.username);
            password = findViewById(R.id.password);
            loginButton = findViewById(R.id.loginButton);
            loginButton.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View view) {
                    if (username.getText().toString().equals("user") && password.getText().toString().equals("1234")) {
                        Toast.makeText(MainActivity.this, "Login Successful!", Toast.LENGTH_SHORT).show();
                    } else {
                        Toast.makeText(MainActivity.this, "Login Failed!", Toast.LENGTH_SHORT).show();
                    }
                }
            });
        }
    }

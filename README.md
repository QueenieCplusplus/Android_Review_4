# Android_Review_4
RadioButton

1. design a layout that includes data, ScrollView, ImageView, TextView and Radio Buttons wrappered in RadioGroup, and then a button at the bottom of the layout which has submit function.

       // fragment_questioner.xml
       <?xml encoding="utf-8"?>
       <layout
        xmlns:android=""
        xmlns:app=""
        xmlns:tools=""
        tools:context="com.example.android.katesapp.QuestionShuffler"
       >
       
         <data>
          <variable
            name=""
            type="om.example.android.katesapp.QuestionFragment"
          />
         </data>
         
         <ScrollView>
         
            <android.constraintlayout.widget.ConstraintLayout
              android:id="@+id/frameLayout"
            >
            
              <ImageView/>
              
              <TextView/>
              
              <RadioGroup
                  android:id="@+id/questionRadioGroup"
              >
              
                  <RadioButton
                     android:id="@+id/firstAns"
                     android:text="@{game.ans[0]}"
                  />
                  
                  <RadioButton
                      android:id="@+id/secAns"
                      android:text="@{game.ans[1]}"
                  />
                  
                  <RadioButton
                      android:id="@+id/thirdAns"
                      android:text="@{game.ans[2]}"
                  />
                  
              
              </RadioGroup>
              
              <Button
                  android:id="@+id/submitButton"
                  android:text="@string/submit_button"
              />
              
         
            </android.constraintlayout.widget.ConstraintLayout>
         
         </ScrollView>
      
       </layout>


2. setup of properties of the UI layout.

   https://github.com/google-developer-training/android-kotlin-fundamentals-apps/blob/master/AndroidTriviaNavigation/app/src/main/res/layout/fragment_game.xml

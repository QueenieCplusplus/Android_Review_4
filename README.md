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
            name="quesitoner" #the instance of class called QuestionFragment
            type="com.example.android.katesapp.QuestionFragment"
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
                     android:text="@{Quesitoner.ans[0]}"
                  />
                  
                  <RadioButton
                      android:id="@+id/secAns"
                      android:text="@{Quesitoner.ans[1]}"
                  />
                  
                  <RadioButton
                      android:id="@+id/thirdAns"
                      android:text="@{Quesitoner.ans[2]}"
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
   
3. code.

       //QuestionerFragment.kt
       
       package com.example.android.katesapp
       
       [default modules]
       import android.os.Bundle
       import androidx.appcompat.app.AppCompatActivity
       
       [fragment modules]
       import androidx.fragment.app.Fragment
       
       [layout inflator modules]
       import android.view.LayoutInflater
       
       [RadioGroup modules]
       import android.view.View
       import android.view.ViewGroup
       
       [Navigation module]
       import androidx.navigation.findNavController
       
       [databinding module]
       import androidx.appcompat.app.AppCompatActivity
       import com.example.android.katesappp.databinding.FragmentQuestionBinding
       
       class QuestionFragment: Fragment() {
       
           data class Question(
              val text: String,
              val ans: List<String>
           )
           
           // TODO: 
           
           // TODO: val declaration and defination hereby
           
           
           override fun onCreateView(inflater: LayoutInflater, container: ViewGroup?, savedInstanceState: Bundle?): View? {
           
               val binding = DataBindingUtil.inflate<FragmentQuestionBinding>(
                     inflater, R.layout.fragment_quesiton, container, false
               )
               
               methodCalled()
               
               
               // bind the class to the layout
               // see data variable name in UI layout
               binding.question = this
               
               
               binding.submitButton.setOnClickListener {
               
               }
           
           
           
          
           
           
           }
       
           private fun methodCalled(){
           
           }
       
       }


4. today's tip (list)

   https://medium.com/chikuwa-tech-study/kotlin-第5課-集合-107be530cdfa
   
5. today's tip (lambda)

   https://medium.com/@louis383/初探-kotlin-lambda-表達式-cfe8796c9fac

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
              
              <TextView
                  android:id="@+id/qTest"
                  android:text="@{qustioner.currentQ.text}"
              />
              
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
       
           // declaration for pushing data
           data class Q(
              val text: String,
              val ans: List<String>
           )
           
           // definition for pushing data
           // ans mean choices hereby
           private val qs: MutableList<Q> = MutableLostOf(
           
              Q(text = "what is your favorite animal?", ans = ListOf("cat", "dog", "fish")),
              Q(text = "what is your davorite color?", ans = ListOf("red", "yellow", "blue")),
              Q(text = "what is your favorite country?", ans = ListOf("USA", "GERMANY", "JP"))
           
           )
           
           lateinit var currentQ: Q
           lateinit var ans: MutableList<String>
           private var qIndex = 0
           
           // shuffle feature
           private numQs = Math.min((qs.size + 1)/2, 3)
           
           
           override fun onCreateView(inflater: LayoutInflater, container: ViewGroup?, savedInstanceState: Bundle?): View? {
           
               val binding = DataBindingUtil.inflate<FragmentQuestionBinding>(
                     inflater, R.layout.fragment_quesiton, container, false
               )
               
               //methodCalled()
               randomQ()
               
               
               // bind the class to the layout
               // see data variable name in UI layout
               binding.question = this
               
               
               // TODO: submit button
               binding.submitButton.setOnClickListener {
               
                 //lambda
                 view: View -> 
                     val checkedId = binding.questionRadioGroup.checkedRadioButtonId
                     
                     // checksom
                     if (-1 != checkedId) {
                     
                            // app's choices push
                            var ansIndex = 0
                            
                            when(checkedId) {
                            
                               R.id.fisrtAns -> ansIndex = 0
                               R.id.secondAns -> ansIndex = 1
                               R.id.thirdAns -> ansIndex = 2
                            
                            } 
                            
                            // other inspection process
                            // TODO
                            
                            if (ans[ansIndex] == currentQ.ans[x]){
                               
                               qInex++
                                
                                // advance to the next question
                                currentQ = qs[qIndex]
                                showQ()
                                binding.invaliateAll()
                                
                                
                               
                            
                            } else {
                            
                                view.findNavController()
                                .navigate()
                            
                            }
                            
                     }   
                     
               }
           
               return binding.root
           
           }
           
           private fun randomQ(){
           
              qs.shuffle
              qIndex = 0
              showQ()
              
           }
       
           private fun showQ(){
           
              currentQ = qs[qIndex]
              ans = currentQ.ans.toMutableList
              ans.shuffle()
           
           }
       
       }


4. today's tip ( kotlin 的 list 類似 Java 的 ArrayList )

   集合的容量比陣列方便，因為無需定義容量。

   https://medium.com/chikuwa-tech-study/kotlin-第5課-集合-107be530cdfa
   
5. today's tip (lambda expression the arrow)

       val lambda = { a:String -> "hi!" }
       
       (a:String) -> { "hi!" }
       
       { p1, p2, p3 -> return result }
       
       (Parameters) -> { Body } 
       
   Basically, the -> separates the parameters (left-side) from the implementation (right side).
   where the -> separates parameters and lambda expression body.

   The parameters are enclosed in parentheses which is the same way as for methods and the lambda expression body is a block of code enclosed in braces.

   https://medium.com/@louis383/初探-kotlin-lambda-表達式-cfe8796c9fac
   
   https://stackoverflow.com/questions/42646016/what-does-the-arrow-operator-do-in-kotlin
   
  6. today's tip (radio button)
  
     https://developer.android.com/guide/topics/ui/controls/radiobutton

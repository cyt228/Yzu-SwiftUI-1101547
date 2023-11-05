<h1>bonus</h1>
<table>
  <tr>
    <td>
      <img src="https://github.com/cyt228/Yzu-SwiftUI-1101547/blob/6f68071d41d7f22b637d69c7b88b74000a690110/RPReplay_Final1699180664.mov">
    </td>
    <td>
      
  ```swift
    import SwiftUI

    struct ContentView: View { 
    
    let displayFontType=[".default",".round",".monospaces","serif"]
    @State var displayFontselected=0
    @State var IsDeepScheme=false
    @State var colorArray:Array=[255.0,255.0,255.0]
    @State var stepperValue=0
    @State var sliderValue=0.0
    @State var selectedDate = Date()
    var body: some View{
        NavigationView{
            Form(
                content: {
                    Section(header:Text("Font settings"),content:{
                        Picker(selection:$displayFontselected,label:Text("Font choice(\(displayFontselected))"),content:{
                            ForEach(0..<displayFontType.count,id:\.self,content: {
                                Text(self.displayFontType[$0])
                            })
                        })
                    })
                    Section(header:Text("background style"),content: {
                        Toggle(isOn:$IsDeepScheme,label:{Text("dark(\(String(IsDeepScheme))")
                        })
                    })
                    Section(header:Text("Stepper")){
                        Stepper("Stepper(\(stepperValue))",
                                onIncrement:{stepperValue+=1},
                                onDecrement:{stepperValue-=1})
                    }
                    Section(header:Text("Slider(\(sliderValue,specifier:"%.2f"))")){
                        Slider(value:$sliderValue,in:0...1)
                    }
                    Section(header: Text("Date Picker")) {
                        DatePicker("Selected Date", selection: $selectedDate, displayedComponents: .date)
                            .datePickerStyle(GraphicalDatePickerStyle())
                            .onChange(of: selectedDate) { newValue in
                                print("Selected Date: \(newValue)")
                            }
                    }
                })
            .navigationBarTitle("Settings")
            }
        }
    }
  ```
    
  </td>
  </tr>
</table>

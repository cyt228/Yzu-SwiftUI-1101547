<h1>HW4</h1>
<table>
  <tr>
    <td>
      <img src="http://raw.githubusercontent.com/cyt228/Yzu-SwiftUI-1101547/main/IMG_0491.gif">
    </td>
    <td>
    <h3>MyApp</h3>
      
 ```swift
    import SwiftUI

    @main
    struct MyApp: App {
        var body: some Scene {
            WindowGroup {
                ContentView()
            }
        }
    }
 ```

   <h3>ContentView</h3>
    
 ```swift
    import SwiftUI

    struct ContentView: View {
        var body: some View {
            VStack {
                Text("美食廣場")
                    .font(.largeTitle)
                    .fontWeight(.heavy)
                    .foregroundStyle(.primary)
                    //.padding(.bottom,0)
                    .padding(.top,20)
                TabView{
                    Group{
                        WelcomeView()
                            .tabItem{
                                Image(systemName: "house")
                                Text("Welcome")
                            }
                        ListView()
                            .tabItem{
                                Image(systemName: "list.dash")
                                Text("Resterunt")
                            }
                        CardView()
                            .tabItem{
                                Image(systemName: "fork.knife.circle")
                                Text("Food")
                            }
                        SettingView()
                            .tabItem{
                                Image(systemName: "wrench.fill")
                                Text("Setting")
                            }
                    }
                    .toolbarBackground(Color.black, for: .tabBar)
                    .toolbarBackground(.visible, for: .tabBar)
                }
            }
            .tint(.yellow)
        }
    }
 ```
<h3>WelcomeView</h3>

```swift
    import SwiftUI

struct WelcomeView: View{
    @AppStorage("UserName") var UserName:String = ""
    var body: some View{
        VStack{
            Text(UserName.isEmpty ? "": UserName)
                .font(.system(size:30))
            ZStack{
                Image("FoodMap")
                    .resizable()
                    .aspectRatio(contentMode: .fit)
                /*Image("footprint")
                    .resizable()
                    .aspectRatio(contentMode: .fit)
                    .frame(width: 300)
                    .offset(x:60,y:40)*/
                /*Image("ShoePrint")
                    .resizable()
                    .aspectRatio(contentMode: .fit)
                    .frame(width: 100)
                    .position(x: 220, y:400)
                    .rotationEffect(.degrees(0))
                Image("ShoePrint")
                    .resizable()
                    .aspectRatio(contentMode: .fit)
                    .frame(width: 100)
                    .position(x: 40, y: 125)
                    .rotationEffect(.degrees(-70))
                    .rotation3DEffect(.degrees(180), axis: (x: 0, y: 1, z: 0))
                Image("ShoePrint")
                    .resizable()
                    .aspectRatio(contentMode: .fit)
                    .frame(width: 100)
                    .position(x: 320, y: 280)
                    .rotationEffect(.degrees(-30))
                 */
            }
            //.position(x:190,y:200)
            Text("帶給你各種必吃美食")
                .fontWeight(.heavy)
                .lineSpacing(20)
                .font(.system(size: 32))
                .foregroundColor( .white)
                .frame(width: 350, height: 70, alignment: .center)
            //.background(Color.blue)
            //.cornerRadius(20)
                .multilineTextAlignment(.center)
        }
    }
}
```

<h3>ListView</h3>

```swift
import SwiftUI

struct Restaurant:Identifiable {
    var id = UUID()
    var name:String
    var image:String
    var menu:String
    var description:String
    var spot:String
    var isFeature:Bool
}
//var restaurantName = ["麥當勞","路易莎","星巴克","海底撈","築間","MoMoParadise"]
//var restaurantImage = ["Mac","Louisa","Star","Hotpot2","Hotpot1","Momo"]
var restaurant = [
    Restaurant(name: "麥當勞" ,image: "Mac" ,menu:"MacMenu" ,description: "美式速食餐廳", spot: "B1美食街", isFeature: true),
    Restaurant(name: "路易莎" ,image: "Louisa" ,menu:"LouisaMenu" ,description: "簡餐咖啡廳", spot: "1F面外商店", isFeature: true),
    Restaurant(name: "海底撈" ,image: "Hotpot2" ,menu:"HotpotMenu2" ,description: "火鍋店", spot: "8F美食樓層", isFeature: false),
    Restaurant(name: "築間" ,image: "Hotpot1" ,menu:"HotpotMenu1" ,description: "火鍋店", spot: "9F美食樓層", isFeature: false),
    Restaurant(name: "MoMoParadise" ,image: "Momo" ,menu:"MoMoMenu" ,description: "壽喜燒餐廳", spot: "9F美食樓層", isFeature: false),
]

struct RestaurantDetailView: View{
    @Environment(\.presentationMode) var presentationMode
    var thisRestaurant:Restaurant
    var body: some View{
        ScrollView{
            VStack{
                Image(thisRestaurant.menu)
                    .resizable()
                    .aspectRatio(contentMode: .fill)
                    .clipped()
                Text(thisRestaurant.name)
                    .font(.system(.title, design: .rounded))
                    .fontWeight(.black)
                Spacer()
                Text(thisRestaurant.description)
                    .font(.system(.subheadline, design:.rounded))
                    .fontWeight(.light)
                Spacer()
                Text(thisRestaurant.spot)
                    .font(.system(.subheadline, design:.rounded))
                    .fontWeight(.light)
                Spacer()            }
        }
        .overlay{
            HStack{
                Spacer()
                VStack{
                    Button(action:{
                        self.presentationMode.wrappedValue.dismiss()
                    },label:{
                        Image(systemName:"chevron.down.circle.fill")
                            .font(.largeTitle)
                            .foregroundColor(.white)
                    })
                }
            }
        }
    }
}

struct BasicImageRow: View{
    var thisRestaurant: Restaurant
    var body: some View{
        HStack{
            Image(thisRestaurant.image)
                .resizable()
                .frame(width: 40, height: 40)
                .cornerRadius(5)
            Text(thisRestaurant.name)
        }
    }
}

struct FullImageRow: View{
    var thisRestaurant: Restaurant
    var body: some View{
        ZStack{
            Image(thisRestaurant.image)
                .resizable()
                .frame(height: 180)
                .aspectRatio(contentMode: .fit)
                .cornerRadius(10)
                .overlay(
                    Rectangle()
                        .foregroundColor(.black)
                        .cornerRadius(10)
                        .opacity(0.2)
                )
            Text(thisRestaurant.name)
                .font(.system(.title))
                .fontWeight(.black)
                .foregroundColor(.white)
                .offset(y: 50)
        }
    }
}

struct ListView: View{
    @State var showDetialView = false
    @State var selectedRestaurant:Restaurant?
    var body: some View{
        NavigationView{
            List(restaurant){
                restaurantItem in
                if restaurantItem.isFeature{
                    FullImageRow(thisRestaurant: restaurantItem)
                        .onTapGesture{
                            self.showDetialView = true
                            self.selectedRestaurant = restaurantItem
                        }  
                }else{
                    BasicImageRow(thisRestaurant: restaurantItem)
                        .onTapGesture{
                            self.showDetialView = true
                            self.selectedRestaurant = restaurantItem
                        }
                }
            }
            .sheet(item: self.$selectedRestaurant){
                thisRestaurant in
                RestaurantDetailView(thisRestaurant: thisRestaurant)
            }
            .navigationBarTitle("餐廳列表")
        }
        /*NavigationView{
            List(restaurant){ 
                restaurantItem in
                NavigationLink(
                    destination: RestaurantDetailView(thisRestaurant: restaurantItem), 
                    label: {
                        BasicImageRow(thisRestaurant: restaurantItem)
                    })
            } 
            .navigationTitle("餐廳列表")
        }*/
    }
}
```

<h3>CardView</h3>

```swift
  import SwiftUI

  struct TermAndDescription: Identifiable{
      var id = UUID()
      var name:String
      var image:String
      var description:String
      var spot:String
  }
  
  var myFood = [
      TermAndDescription(name: "麥當勞" ,image: "Mac" ,description: "美式速食餐廳" ,spot: "B1美食街"),
      TermAndDescription(name: "MoMOParadise" ,image: "Momo" ,description: "壽喜燒餐廳" ,spot: "9F美食樓層"),
      TermAndDescription(name: "海底撈" ,image: "Hotpot2" ,description: "火鍋店" ,spot: "8F美食樓層"),
      TermAndDescription(name: "路易莎" ,image: "Louisa" ,description: "簡餐咖啡廳" ,spot: "1F面外商店"),
      TermAndDescription(name: "築間" ,image: "Hotpot1" ,description: "火鍋店" ,spot: "9F美食樓層"),
  ]
  
  struct CardView: View{
      @State var currentCard = Int.random(in: 0...4)
      var body: some View{
          VStack{
              Text("推薦餐廳")
                  .font(.title)
                  .offset(y: -50)
              VStack{
                  Text(myFood[currentCard].name)
                      .font(.headline)
                      //.padding(.all, 5)
                  Image(myFood[currentCard].image)
                      .resizable()
                      .aspectRatio(contentMode: .fill)
                      .clipped()
                  Text(myFood[currentCard].description)
                      .font(.system(.subheadline, design:.rounded))
                      .fontWeight(.light)
                  Text(myFood[currentCard].spot)
                      .font(.system(.subheadline, design:.rounded))
                      .fontWeight(.light)
              }
              .frame(minWidth: 0, idealWidth: 100, maxWidth: 300, minHeight: 0, idealHeight: 100, maxHeight: 300 ,alignment: .center)
              .background(Color.gray)
              .onTapGesture{
                  currentCard = Int.random(in: 0...4)
                  /*if(currentCard < myFood.count - 1){
                      currentCard += 1
                  }
                  else{
                      currentCard = 0
                  }*/
              }
              Text("點擊下一張推薦")
                  .offset(y: 50)
          }
      }
  }
  ```

  <h3>SettingView</h3>
  
   ```swift
      import SwiftUI

      struct SettingView: View { 
          let displayFontType=[".default",".round",".monospaces","serif"]
          @State var displayFontselected=0
          @State var IsDeepScheme=false
          @State var colorArray:Array=[255.0,255.0,255.0]
          @State var stepperValue=0
          @State var sliderValue=0.0
          @AppStorage("UserName") var UserName:String = ""
          var body: some View{
              NavigationView{
                  Form(content: {
                      Section(content:{
                          TextField("請輸入你的名字", text: $UserName)
                      }, header:{
                          Text("使用者名稱")
                      })
                      Section(header:Text("字型設定"),content:{
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
                  })
                  .navigationBarTitle("Settings")
              }
          }
      }
  ```

   </td>
  </tr>
</table>

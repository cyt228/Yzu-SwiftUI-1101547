<h1>HW4</h1>
<table>
  <tr>
    <td>
      <img src="http://raw.githubusercontent.com/cyt228/Yzu-SwiftUI-1101547/main/IMG_0491.gif">
    </td>
    <td>
      <tr>
    <h2>MyApp</h2>
      
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
</tr>
     <h2>ContentView</h2>
    
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

   </td>
  </tr>
</table>

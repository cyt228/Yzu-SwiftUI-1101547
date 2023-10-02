<h1>HW1</h1>
<table>
  <tr>
    <td>
      <img src="https://raw.githubusercontent.com/cyt228/Yzu-SwiftUI-1101547/main/IMG_0363.jpeg">
    </td>
    <td>
      
  ```swift
    import SwiftUI
    struct ContentView: View {
      var body: some View {
        ZStack(alignment: .top){
          Image("Me")
              .resizable()
              .aspectRatio(contentMode: .fit)
              .clipShape(Circle())
              .frame(width: 380,height:400,alignment: .center)
              //.overlay{
          Text(" 1101547 陳釔橦\nStand Out Fit In")
              .font(.system(size:15))
              .frame(width:200,height:50)
              .cornerRadius(3.0)
              .foregroundColor(.brown)
              .fontWeight(.bold)
              .offset(x: 120, y: 160)
                      //.position(x: 310, y: 200)
              //}
              //.overlay{
          Image(systemName: "sparkles")
              .font(.system(size:80))
              .foregroundColor(.yellow)
                 //.opacity(0.9)
                      //.position(x:65,y:70)
              .offset(x: -140, y: 30)
              //}
        }
      }
    }
  ```
    
  </td>
  </tr>
</table>

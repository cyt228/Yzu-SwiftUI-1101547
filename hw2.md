<h1>HW2</h1>
<table>
  <tr>
    <td>
      <img src="">
    </td>
    <td>

  ```swift
    import SwiftUI
    
    struct ContentView: View { 
        @State var count:Int = 0
        @State var count1:Int = 3
        //@State var stringN:String = "Draw"
        var name=["paper","scissor","rock","paperR","scissorR","rockR"]
        var body: some View{
            VStack{
                picView(imageName: name[count1])
                picView(imageName: name[count])
                /*Text(String(count))
                 .padding(.all,10)
                 .frame(width: 150, height: 120,alignment: .center)
                 .font(.system(size: 100))*/
                //Text("\(count1) \(count)")
                if count1 % 3 == count {
                    //stringN = "Draw"
                    Text("Draw")
                        .font(.system(size:30))
                        .padding(.all,5)
                }
                else if (((count1 % 3 == 0) && (count == 2))
                || ((count1 % 3 == 1) && (count == 0))
                || ((count1 % 3 == 2) && (count == 1))){
                    //stringN = "You Lose"
                    Text("You Lose")
                        .font(.system(size:30))
                        .padding(.all,5)
                }
                else{
                    //stringN = "You Win"
                    Text("You Win")
                        .font(.system(size:30))
                        .padding(.all,5)
                }
                //Text(stringN)
                //wordView(strName: stringN)
                HStack{
                    Button(action: {
                        count = 2
                        //count = Int.random(in: 0...2)
                        count1 = Int.random(in: 3...5)
                    }, label: {
                        Text("Rock")
                            .font(.system(size: 30))
                            .padding(.all,10)
                            .frame(width: 100, height: 50, alignment: .center)
                            .background(Color.purple)
                            .foregroundColor(.white)
                            .border(Color.purple, width: 5)
                            .cornerRadius(20)
                    })
                    Button(action: {
                        count = 0
                        //count = Int.random(in: 0...2)
                        count1 = Int.random(in: 3...5)
                    }, label: {
                        Text("Paper")
                            .font(.system(size: 30))
                            .padding(.all,10)
                            .frame(width: 100, height: 50, alignment: .center)
                            .background(Color.purple)
                            .foregroundColor(.white)
                            .border(Color.purple, width: 5)
                            .cornerRadius(20)
                    })
                    Button(action: {
                        count = 1
                        //count = Int.random(in: 0...2)
                        count1 = Int.random(in: 3...5)
                    }, label: {
                        Text("Scissor")
                            .font(.system(size: 30))
                            .padding(.all,10)
                            .frame(width: 130, height: 50, alignment: .center)
                            .background(Color.purple)
                            .foregroundColor(.white)
                            .border(Color.purple, width: 5)
                            .cornerRadius(20)
                    })
                }
            }
        }
    }
    struct picView: View{
        var imageName: String
        var body: some View{
            Image(imageName)
                .resizable()
                .aspectRatio(contentMode: .fit)
                .clipShape(Circle())
                .frame(width: 300)
        }
    }
    
    /*struct wordView: View{
        var strName: String
        var body: some View{
            Text(strName)
            
        }
    }*/
  ```

  </td>
  </tr>
</table>

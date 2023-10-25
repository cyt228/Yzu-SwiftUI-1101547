<h1>HW3</h1>
<table>
  <tr>
    <td>
      <img src="http://raw.githubusercontent.com/cyt228/Yzu-SwiftUI-1101547/main/IMG_0401.jpeg">
    </td>
    <td>

      ```swift
        import SwiftUI

        struct ContentView: View {
            var body: some View {
                VStack{
                    TitleView()
                        .offset(y: 50)
                    ZStack{
                        Image("Back")
                            .resizable()
                            .aspectRatio(contentMode: .fit)
                            .frame(width: UIScreen.screenWidth,
                                   height: UIScreen.screenHeight-225)
                        HStack{
                            //TomatoView()
                            //BananaView()
                            ZStack{
                                //CupView(imageName: "Cup", m: 240)
                                CupView(imageName: "Cup", m: 200)
                                CupView(imageName: "Cup", m: 160)
                                CupView(imageName: "Cup", m: 120)
                                CupView(imageName: "Cup", m: 75)
                                CupView(imageName: "Cup", m: 25)
                                CupView(imageName: "Cup", m: -25)
                            }
                            .offset(x: 23 ,y: -150)
                            ZStack{
                                CandyView(imageName: "Candy1", m: 0)
                                CandyView(imageName: "Candy2", m: 25)
                                CandyView(imageName: "Candy3", m: 50)
                                CandyView(imageName: "Candy4", m: 75)
                                //CandyView(imageName: "Candy5", m: 100)
                            }
                            .offset(x: -35 ,y: -150)
                            ChipView(imageName: "Cheetos")
                                .offset(x: 5 ,y: -150)
                        }
                        HStack{
                            ZStack{
                                Chip2View(imageName: "Doritos1", m: 0)
                                Chip2View(imageName: "Doritos2", m: 25)
                            }
                            .offset(x: 85, y: 70)
                            Chip3View(imageName: "Pringles")
                                .offset(x: 50 ,y: 100)
                        }
                        HStack{
                            ZStack{
                                ChocoView(imageName: "Choco1", m: 0)
                                ChocoView(imageName: "Choco3", m: 25)
                                ChocoView(imageName: "Choco2", m: 50)
                                ChocoView(imageName: "Choco4", m: 75)
                            }
                            .offset(x: -90 ,y: 175)
                            
                        }
                    }
                }
                //.offset(y :170)
            }
        }
        
        struct TitleView: View{
            var body: some View{
                VStack(alignment: .center, spacing: 2){
                    Text("CYT")
                        .font(.system(size:30))
                    Text("零食櫃")
                        .font(.title)
                        /*.foregroundColor(Color(red: 190/255, green: 180/255, blue: 80/255))*/
                }
            }
        }
        
        struct CandyView: View{
            var imageName: String
            var m:Int
            var body: some View{
                VStack{
                    Image(imageName)
                        .resizable()
                        .aspectRatio(contentMode: .fit)
                        .frame(width: /*100*/UIScreen.screenWidth/7-100,
                               height: UIScreen.screenHeight/4,
                               alignment: .center)
                        .offset(x:CGFloat(m))
                }.padding(.all, 2)
                Text("Candys"/*imageName*//*.capitalized*/)
                    .fontWeight(.bold)
                    .font(.system(size: 20))
                    .offset(x: 45, y: 45)
            }
        }
        
        struct CupView: View{
            var imageName: String
            var m:Int
            var body: some View{
                VStack{
                    Image(imageName)
                        .resizable()
                        .aspectRatio(contentMode: .fit)
                        .frame(width: /*100*/UIScreen.screenWidth/7-25,
                               height: UIScreen.screenHeight/4,
                               alignment: .center)
                        .offset(x: -25, y: CGFloat(m))
                    Text("Cup Noodles"/*imageName*//*.capitalized*/)
                        .fontWeight(.bold)
                        .font(.system(size: 20))
                        .offset(x: -20, y: 135)
                }.padding(.all, 2)
            }
        }
        
        struct ChipView: View{
            var imageName: String
            var body: some View{
                VStack{
                    Image(imageName)
                        .resizable()
                        .aspectRatio(contentMode: .fit)
                        .frame(width: /*100*/UIScreen.screenWidth/7-25,
                               height: UIScreen.screenHeight/4-50,
                               alignment: .center)
                    Text(imageName/*.capitalized*/)
                        .fontWeight(.bold)
                        .font(.system(size: 20))
                        .offset(y: -20)
                }.padding(.all, 2)
            }
        }
        
        struct Chip2View: View{
            var imageName: String
            var m:Int
            var body: some View{
                VStack{
                    Image(imageName)
                        .resizable()
                        .aspectRatio(contentMode: .fit)
                        .frame(width: /*100*/UIScreen.screenWidth/7-50+CGFloat(m),
                               alignment: .center)
                        .offset(x: CGFloat(m), y: -60)
                }.padding(.all, 2)
                Text("Doritos"/*imageName*//*.capitalized*/)
                    .fontWeight(.bold)
                    .font(.system(size: 20))
                    .offset(x: 10, y: 25)
            }
        }
        
        struct Chip3View: View{
            var imageName: String
            var body: some View{
                VStack{
                    Image(imageName)
                        .resizable()
                        .aspectRatio(contentMode: .fit)
                        .frame(width: UIScreen.screenWidth/7,
                               height: UIScreen.screenHeight/3+50,
                               alignment: .center)
                    Text("Pringles"/*.capitalized*/)
                        .fontWeight(.bold)
                        .font(.system(size: 20))
                        .offset(y: -35)
                }.padding(.all, 2)
            }
        }
        
        struct ChocoView: View{
            var imageName: String
            var m:Int
            var body: some View{
                VStack{
                    Image(imageName)
                        .resizable()
                        .aspectRatio(contentMode: .fit)
                        .frame(width: /*100*/UIScreen.screenWidth/3,
                               height: UIScreen.screenHeight/4,
                               alignment: .center)
                        .offset(x:CGFloat(m))
                }.padding(.all, 2)
                Text("Coco"/*imageName*//*.capitalized*/)
                    .fontWeight(.bold)
                    .font(.system(size: 20))
                    .offset(x:50 ,y: 70)
            }
        }
        
        extension UIScreen{
            static let screenWidth = UIScreen.main.bounds.size.width
            static let screenHeight = UIScreen.main.bounds.size.height
            static let screenSize = UIScreen.main.bounds.size
        }
      ```

    </td>
  </tr>
</table>

# SwiftUIDialogScaffold

```swift
        ZStack {
            
            BackgroundColor
                .ignoresSafeArea()
                .opacity(show ? 1 : 0)
                .animation(.easeInOut(duration: 0.8))
                .onTapGesture {
                    show = false
                }
            
            VStack(spacing: 0) {
                

                
                CustomButton {
                    show = false
                    onConfirm()
                } content: {
                    Text("확인")
                        .foregroundColor(.white)
                        .fontWeight(.semibold)
                        .adaptiveFontSize(16)
                        .adaptiveHeight(58)
                        .frame(maxWidth: .infinity)
                        .background(Color(red: 72/255, green: 118/255, blue: 238/255))
                        .cornerRadius(12)
                        .adaptivePadding(base: .width, .horizontal, 18)
                        .adaptivePadding(.bottom, 20)
                }
                
            } //: VSTACK
            .frame(maxWidth: .infinity)
            .background(Color(red: 26/255, green: 26/255, blue: 26/255))
            .cornerRadius(8)
            .adaptivePadding(base: .width, .horizontal, 24)
            .offset(y: show ? 0 : UIScreen.main.bounds.height)
            .animation(.interpolatingSpring(mass: 1, stiffness: 100, damping: 20, initialVelocity: 0))
        } //: ZSTACK
```

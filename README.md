# SwiftUIDialogScaffold

```swift
struct DialogView: View {
    
    let backgroundColor: Color
    let foregroundColor: Color
    let horizontalPadding: CGFloat
    @State private var animate: Bool = false
    @Binding var show: Bool
    let onConfirm: () -> Void
    
    var body: some View {
        ZStack {
            
            backgroundColor
                .ignoresSafeArea()
                .opacity(animate ? 1 : 0)
                .animation(.easeInOut(duration: 0.8))
            
            VStack(spacing: 0) {
                
                VStack(spacing: 0) {
                                      
//                    Button {
//                        FeedbackGenerator.generate()
//                        animate = false
//                        DispatchQueue.main.asyncAfter(deadline: .now() + 1) {
//                            self.show.toggle()
//                            onConfirm()
//                        }
//                    } label: {
//                        Text("OK")
//                    }
//                    .buttonStyle(PlainButtonStyle())
                    
                }
                
            } //: VSTACK
            .background(foregroundColor)
            .cornerRadius(16)
            .padding(.horizontal, horizontalPadding)
            .offset(y: animate ? 0 : UIScreen.main.bounds.height)
            .animation(.interpolatingSpring(mass: 1, stiffness: 100, damping: 20, initialVelocity: 0))
            .onAppear {
                animate = true
            }
        } //: ZSTACK
    }
}
```

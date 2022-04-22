# SwiftUIDialogScaffold

```swift
struct CalendarDialog: View {
    
    @Binding var show: Bool
    @Binding var currentDate: Date
    let onDayClick: (Date) -> Void
    
    @GestureState private var gestureOffset: CGFloat = 0
    @State private var draggedOffset: CGSize = .zero
    
    var body: some View {
        
        
        VStack(spacing: 0) {
            
            Spacer()
            
            VStack(spacing: 0) {
                Capsule()
                    .foregroundColor(Color(red: 229/255, green: 229/255, blue: 235/255))
                    .frame(width: 75, height: 5)
                    .adaptivePadding(.top, 16)
                    .adaptivePadding(.bottom, 27)
                
                
                CustomDatePicker(currentDate: $currentDate,
                                 onDayClick: { date in
                    onDayClick(date)
                })
                .adaptivePadding(.horizontal, 37)
                .adaptivePadding(.bottom, 24)
                
                HStack(spacing: 0) {
                    CustomButton {
                        show = false
                    } content: {
                        Text("취소")
                            .foregroundColor(Color(red: 51/255, green: 51/255, blue: 51/255))
                            .adaptiveFrame(width: 100, height: 40)
                            .background(Color.clear)
                            .cornerRadius(5)
                            .adaptiveFontSize(14)
                    }
                    
                    Spacer()
                    
                    CustomButton {
                        show = false
                    } content: {
                        Text("선택")
                            .foregroundColor(.white)
                            .adaptiveFrame(width: 100, height: 40)
                            .background(Color(red: 0/255, green: 149/255, blue: 255/255))
                            .cornerRadius(5)
                            .adaptiveFontSize(14)
                    }
                    
                }
                .adaptivePadding(.horizontal, 41)
                .adaptivePadding(.bottom, 51.8)
                
                
            } //: VSTACK
            .animation(.spring())
            .frame(maxWidth: .infinity, alignment: .bottom)
            .background(
                RoundedRectangle(cornerRadius: 25)
                    .fill(Color.white)
                    .shadow(color: .gray, radius: 10, x: 0, y: 2)
            )
            .offset(y: self.draggedOffset.height)
            .gesture(
                DragGesture()
                    .onChanged { value in
                        if value.translation.height > 0 {
                            self.draggedOffset = value.translation
                        }
                    }
                    .onEnded { value in
                        
                        if value.translation.height > UIScreen.main.bounds.height / 5 {
                            self.draggedOffset = .zero
                            show = false
                            return
                        }
                        self.draggedOffset = .zero
                    }
            )
    
            
        } //: VSTACK
        .ignoresSafeArea()
        .offset(y: show ? 0 : UIScreen.main.bounds.height)
    }
}
```

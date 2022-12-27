# ImageClassificationSwiftUI

Core MLモデル  
https://developer.apple.com/jp/machine-learning/models/

### Download Model
<img width="865" alt="機械学習_-_モデル_-_Apple_Developer" src="https://user-images.githubusercontent.com/47273077/209615671-2d89f22d-eeea-450e-8986-078ecdec3618.png">


### Place Model into Project
<img width="299" alt="ImageClassificationSwiftUI_—_MobileNetV2_と_New_File" src="https://user-images.githubusercontent.com/47273077/209615834-faf7bb0e-bde6-4867-ad7e-64495be8f1f8.png">

```swift
 @State private var classficationLabel: String = ""
    
    let model = MobileNetV2()
    
    private func performImageClassfication() {
        
        let currentImageName = photos[currentIndex]
        
        guard let img = UIImage(named: currentImageName),
              let resizedImage = img.resizeTo(size: CGSize(width: 224, height: 224)),
              let buffer = resizedImage.toBuffer() else {
            return
        }
        
        let output = try? model.prediction(image: buffer)
        
        if let output = output {
            
            self.classficationLabel = output.classLabel
        }
        
    }
  
  ```

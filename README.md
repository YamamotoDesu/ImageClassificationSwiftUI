# ImageClassificationSwiftUI
<img width="300" alt="スクリーンショット 2022-12-27 15 20 52" src="https://user-images.githubusercontent.com/47273077/209620812-1c661526-ac74-421a-97a0-06f4fed881f1.gif">

Core MLモデル  
https://developer.apple.com/jp/machine-learning/models/

### Download Model
<img width="865" alt="機械学習_-_モデル_-_Apple_Developer" src="https://user-images.githubusercontent.com/47273077/209615671-2d89f22d-eeea-450e-8986-078ecdec3618.png">


### Place Model into Project
<img width="299" alt="ImageClassificationSwiftUI_—_MobileNetV2_と_New_File" src="https://user-images.githubusercontent.com/47273077/209615834-faf7bb0e-bde6-4867-ad7e-64495be8f1f8.png">

### Classfy the image

<img width="454" alt="ImageClassificationSwiftUI_—_MobileNetV2" src="https://user-images.githubusercontent.com/47273077/209619642-eb1cca9c-ac91-4bdb-b5e1-de57b11b2a96.png">

<img width="825" alt="スクリーンショット_2022_12_27_15_25" src="https://user-images.githubusercontent.com/47273077/209621386-95cb434d-bf07-44d1-a911-9766d8f37f66.png">

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
  
### How to classfy Images
```swift
  
             let results = output.classLabelProbs.sorted { $0.value > $1.value }
            
          let result = results.map { key, value in
             return "\(key) = \(value * 100)"
           }.joined(separator: "\n")
  ```
   
   
 <img width="372" alt="スクリーンショット_2022_12_27_15_48" src="https://user-images.githubusercontent.com/47273077/209624129-41ea74a0-8bc4-42b8-b1cf-98f95a85b707.png">

  

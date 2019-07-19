# ImagePickerController

### 1. Intro to Image Picker Controller
Image Picker Controller allows the user to access their media library to upload certain images to the app memory. In our example, we called ```addNewPerson()``` function using selector method from a navigation bar item.

```swift
@objc func addNewPerson() {
        let picker = UIImagePickerController()
        picker.allowsEditing = true
        picker.delegate = self
        present(picker, animated: true)
    }
```
If we simply use this, it will trigger an error. Our view controller needs to be recognised as a delegate for both UIImagePickerController and UINavigationController
```swift
class ViewController: UIViewController, UIImagePickerControllerDelegate, UINavigationControllerDelegate
```

### 2. Working with the Selected Image
The UIImagePickerController simply allows us to access the UI Image Picker interface. To work with the image itself, we need to include several methods:
```swift
func imagePickerController(_ picker: UIImagePickerController, didFinishPickingMediaWithInfo info: [UIImagePickerController.InfoKey : Any]) {
        guard let image = info[.editedImage] as? UIImage else {return}
        
        let imageName = UUID().uuidString
        let imagePath = getDocumentsDirectory().appendingPathComponent(imageName) // adds imageName to the path
        
        if let jpegData = image.jpegData(compressionQuality: 0.8) {
            try? jpegData.write(to: imagePath)
        }
        dismiss(animated: true)
}
```
This does a few things:
1. Calls protocol method from UIIMagePickerController
2. ```guard``` method to receive the UIImage safely
3. Assign unique ID to save the imageName
4. Write the image as a JPEG to the imagePath
  
The method ```getDocumentsDirectory() is as follows:
```swift
func getDocumentsDirectory() -> URL {
        let paths = FileManager.default.urls(for: .documentDirectory, in: .userDomainMask)
        return paths[0]
    }
```

        
        
        

# ToneCurve


you can use .acv file from photoshop 

ACVParcer can read .acv file and create data to input CIColorCubeWithColorSpace Filter
        
        let parcer = ACVParcer(with: "vintage.acv")
        let data = parcer.createColorCubeData()

following is a usual process
https://developer.apple.com/library/content/documentation/GraphicsImaging/Reference/CoreImageFilterReference/index.html#//apple_ref/doc/filter/ci/CIColorCubeWithColorSpace

        let image = UIImage(named: "image.png")!
        let inputImage = CIImage(cgImage:  image.cgImage!)
        
        let filter = CIFilter(name: "CIColorCubeWithColorSpace")!
        filter.setValue(inputImage, forKey: "inputImage")
        filter.setValue(32, forKey: "inputCubeDimension")
        filter.setValue(data, forKey: "inputCubeData")
        filter.setValue(CGColorSpaceCreateDeviceRGB(), forKey: "inputColorSpace")
        
        let output = filter.outputImage!
        
        let context = CIContext()
        let imageRef = context.createCGImage(output, from: output.extent)!
        let outputImage = UIImage(cgImage: imageRef)
        
        
 this is just a sample 

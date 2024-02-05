# PrepareForDisplay
Decodes an image asynchronously and provides a new one for display in views and animations.
Facing issues or laggy animations or scrolling of collection view cell like things when loading big images ?

So here is the solution

# Common Approach

import UIKit
let image = UIImage (named: "big-image")
imageView-image = image


# Other Approach but It may lead to thread crash sometimes
import UIKit
let image = UIImage(named: "big-image")
DispatchQueue.global().async {
self.imageView.image = image
}// off loading the heavy work to background
Now, better approach

import UIKit
let image = UIImage (named: "big-image")
image?-prepareForDisplay { Iweak selfl preparedImage
DispatchQueue.main.async {
self?. imageView. image = preparedImage
}
}

# Above approach with Swift Concurrency

import UIKit
let image = UIImage (named: "big-image")
Task {
imageView image = await image?.byPreparingForDisplay()
}
You can also create a thumbnail using func prepareThumbnail(of: CGSize, completionHandler: (UIImage?) -> Void) of specific size

![Simulator Screen Recording - iPhone 15 Pro - 2024-02-05 at 15 40 26](https://github.com/nbnitin/PrepareForDisplay/assets/5785670/3f9500e4-f9ed-4f0e-ab87-78d01dcafd55)



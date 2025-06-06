# Capacitor Document Scanner

[![Npm package version](https://img.shields.io/npm/v/@therealabdi27/capacitor-document-scanner-v2/latest.svg?style=for-the-badge&logo=npm)](https://www.npmjs.com/package/@therealabdi27/capacitor-document-scanner-v2)

This is a Capacitor plugin that lets you scan documents using Android and iOS. You can use it to create
apps that let users scan notes, homework, business cards, receipts, or anything with a rectangular shape.

## Fork Information

This is a fork of [WebsiteBeaver/capacitor-document-scanner](https://github.com/WebsiteBeaver/capacitor-document-scanner).

**Reason for fork:** The original project is no longer maintained and doesn't support Capacitor 6, or 7 in its peer dependencies. This fork has been updated to include support for Capacitor 6, and 7, ensuring compatibility with modern Capacitor applications.

| iOS                                                                                                                  | Android                                                                                                                  |
| -------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| ![Dollar-iOS](https://user-images.githubusercontent.com/26162804/160485984-e6c46563-56ee-4be9-b241-34a186e0029d.gif) | ![Dollar Android](https://user-images.githubusercontent.com/26162804/160306955-af9c5dd6-5cdf-4e2c-8770-c734a594985d.gif) |

## Install

```bash
npm install capacitor-document-scanner
npx cap sync
```

## Examples

* [Basic Example](#basic-example)
* [Limit Number of Scans](#limit-number-of-scans)
* [Remove Cropper](#remove-cropper)

### Basic Example

```typescript
import { Capacitor } from '@capacitor/core'
import { DocumentScanner } from 'capacitor-document-scanner'

const scanDocument = async () => {
  // start the document scanner
  const { scannedImages } = await DocumentScanner.scanDocument()

  // get back an array with scanned image file paths
  if (scannedImages.length > 0) {
    // set the img src, so we can view the first scanned image
    const scannedImage = document.getElementById('scannedImage') as HTMLImageElement
    scannedImage.src = Capacitor.convertFileSrc(scannedImages[0])
  }
}
```

Here's what this example looks like with several items

https://user-images.githubusercontent.com/26162804/160264220-0a77a55c-33b1-492a-9617-6d2c083b0583.mp4

https://user-images.githubusercontent.com/26162804/160264222-bef1ba3d-d6c1-43c8-ba2e-77ff5baef836.mp4

https://user-images.githubusercontent.com/26162804/161643046-57536193-0c6c-4edf-8f29-6f3ef9854dc5.mp4

https://user-images.githubusercontent.com/26162804/161643075-365b5008-4bc8-4507-969d-b2c188f372ec.mp4

https://user-images.githubusercontent.com/26162804/161643102-35283536-73a3-4b05-bd76-c06514ca3928.mp4

https://user-images.githubusercontent.com/26162804/161643126-f5c2461d-768d-481c-8dee-4d74a0cae778.mp4

https://user-images.githubusercontent.com/26162804/161643156-4ce1abac-d78b-4211-a99a-f0bebd40e2a6.mp4

https://user-images.githubusercontent.com/26162804/161643167-fc751455-1a1a-4b1c-b06f-a3a2cef0d0b0.mp4

https://user-images.githubusercontent.com/26162804/161643192-71db71af-392d-4b6a-b94d-851a3369dbf3.mp4

https://user-images.githubusercontent.com/26162804/161643203-2a265cc1-5cf1-4474-b43c-7b1b2dcba704.mp4

### Limit Number of Scans

You can limit the number of scans. For example if your app lets a user scan a business 
card you might want them to only capture the front and back. In this case you can set
maxNumDocuments to 2. This only works on Android.

```typescript
import { Capacitor } from '@capacitor/core'
import { DocumentScanner } from 'capacitor-document-scanner'

const scanDocument = async () => {
  // limit the number of scans to 2
  const { scannedImages } = await DocumentScanner.scanDocument({
    maxNumDocuments: 2
  })

  // get back an array with scanned image file paths
  if (scannedImages.length > 0) {
    // set the img src, so we can view the first scanned image
    const scannedImage = document.getElementById('scannedImage') as HTMLImageElement
    scannedImage.src = Capacitor.convertFileSrc(scannedImages[0])
  }
}
```

https://user-images.githubusercontent.com/26162804/161643345-6fe15f33-9414-46f5-b5d5-24d88948e801.mp4

### Remove Cropper

You can automatically accept the detected document corners, and prevent the user from 
making adjustments. Set letUserAdjustCrop to false to skip the crop screen. This limits
the max number of scans to 1. This only works on Android.

```typescript
import { Capacitor } from '@capacitor/core'
import { DocumentScanner } from 'capacitor-document-scanner'

const scanDocument = async () => {
  // skip the crop screen
  const { scannedImages } = await DocumentScanner.scanDocument({
    letUserAdjustCrop: false
  })

  // get back an array with scanned image file paths
  if (scannedImages.length > 0) {
    // set the img src, so we can view the first scanned image
    const scannedImage = document.getElementById('scannedImage') as HTMLImageElement
    scannedImage.src = Capacitor.convertFileSrc(scannedImages[0])
  }
}
```

https://user-images.githubusercontent.com/26162804/161643377-cabd7f51-a16f-4f5e-938a-afb6f3b1c8cb.mp4

## iOS

iOS requires the following usage description be added and filled out for your app in `Info.plist`:

- `NSCameraUsageDescription` (`Privacy - Camera Usage Description`)

Read about [Configuring `Info.plist`](https://capacitorjs.com/docs/ios/configuration#configuring-infoplist) in the [iOS Guide](https://capacitorjs.com/docs/ios) for more information on setting iOS permissions in Xcode

## Documentation

<docgen-index>

* [`scanDocument(...)`](#scandocument)
* [Interfaces](#interfaces)
* [Enums](#enums)

</docgen-index>

<docgen-api>
<!--Update the source file JSDoc comments and rerun docgen to update the docs below-->

### scanDocument(...)

```typescript
scanDocument(options?: ScanDocumentOptions | undefined) => Promise<ScanDocumentResponse>
```

Opens the camera, and starts the document scan

| Param         | Type                                                                |
| ------------- | ------------------------------------------------------------------- |
| **`options`** | <code><a href="#scandocumentoptions">ScanDocumentOptions</a></code> |

**Returns:** <code>Promise&lt;<a href="#scandocumentresponse">ScanDocumentResponse</a>&gt;</code>

--------------------


### Interfaces


#### ScanDocumentResponse

| Prop                | Type                                                                              | Description                                                                                                                       |
| ------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| **`scannedImages`** | <code>string[]</code>                                                             | This is an array with either file paths or base64 images for the document scan.                                                   |
| **`status`**        | <code><a href="#scandocumentresponsestatus">ScanDocumentResponseStatus</a></code> | The status lets you know if the document scan completes successfully, or if the user cancels before completing the document scan. |


#### ScanDocumentOptions

| Prop                      | Type                                                  | Description                                                                                                                                                                                                                                                                                                                               | Default                                   |
| ------------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------- |
| **`croppedImageQuality`** | <code>number</code>                                   | Android only: The quality of the cropped image from 0 - 100. 100 is the best quality.                                                                                                                                                                                                                                                     | <code>: 100</code>                        |
| **`letUserAdjustCrop`**   | <code>boolean</code>                                  | Android only: If true then once the user takes a photo, they get to preview the automatically detected document corners. They can then move the corners in case there needs to be an adjustment. If false then the user can't adjust the corners, and the user can only take 1 photo (maxNumDocuments can't be more than 1 in this case). | <code>: true</code>                       |
| **`maxNumDocuments`**     | <code>number</code>                                   | Android only: The maximum number of photos an user can take (not counting photo retakes)                                                                                                                                                                                                                                                  | <code>: 24</code>                         |
| **`responseType`**        | <code><a href="#responsetype">ResponseType</a></code> | The response comes back in this format on success. It can be the document scan image file paths or base64 images.                                                                                                                                                                                                                         | <code>: ResponseType.ImageFilePath</code> |


### Enums


#### ScanDocumentResponseStatus

| Members       | Value                  | Description                                                                                               |
| ------------- | ---------------------- | --------------------------------------------------------------------------------------------------------- |
| **`Success`** | <code>'success'</code> | The status comes back as success if the document scan completes successfully.                             |
| **`Cancel`**  | <code>'cancel'</code>  | The status comes back as cancel if the user closes out of the camera before completing the document scan. |


#### ResponseType

| Members             | Value                        | Description                                                                     |
| ------------------- | ---------------------------- | ------------------------------------------------------------------------------- |
| **`Base64`**        | <code>'base64'</code>        | Use this response type if you want document scan returned as base64 images.     |
| **`ImageFilePath`** | <code>'imageFilePath'</code> | Use this response type if you want document scan returned as inmage file paths. |

</docgen-api>

## License

Copyright 2022 David Marcus

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
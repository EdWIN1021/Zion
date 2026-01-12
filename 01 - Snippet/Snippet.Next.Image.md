# Image

```scss
import Image from 'next/image'
import pic from '../assets/pic.png'

<Image
    src={profilePic}
  alt="Picture of the author"
  // width={500} automatically provided
  // height={500} automatically provided
  // blurDataURL="data:..." automatically provided
  // placeholder="blur" // Optional blur-up while loading
    // priority => LCP
/>
```
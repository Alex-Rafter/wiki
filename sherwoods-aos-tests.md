# AOS checks

RE: screenshot provided, this doesn't show a good quality test.
The images are all being loaded from the disk cache so don't represent real world performance, and give a false sense of speed.

When tested from a clear cache, the results would likley be very different.

## AOS Test Results

Testing vehicle : id-235371
URl: 
https://www.sherwoodsmotorgroup.co.uk/used-car-details/used-citroen-c3-aircross-12-puretech-flair-suv-5dr-pet-hatchback-black-manual-petrol/id-235371/

### Image Data
31.4mbs of image data transferred from urls with autosonshow in the url.
Approx 35 images loaded at over 0.5mbs each, and with jpeg type.

This is a very very large amount of image data for a single page relative to our sites not using AOS plugin.

#### Comparison a recent new build not using AOS>
https://www.alexandersmotorgroup.co.uk/used-car-details/used-nissan-micra-12-acenta-5-door-hatchback-shiraz-red-automatic-petrol/id-5219254662445/

loads 996 kB (1mb) of image data for 57 images. Images are using webp format with better compression.
Less than 1/30th of the image data transferred compared to the Sherwoods AOS page above.

#### Image D/L and testing
https://eu.cdn.autosonshow.tv/6775/18149/EG18YTR/main360_27.jpg?d631585349efb2a15c27151a5196712e
image size: 567kb (0.5+mbs) (quite standard for those loaded on test page)
format jpeg
Quickly tested with better compression and using a more modern image format (webp), reduces file size by 80% to 118 kB.

You can run the test yourself quite easily by downloading that same image, uploading it to https://squoosh.app/ and just selecting webp preset. There is little to no visible quality loss at this level of compression.

### JS

567.3kbs of Javascript loaded by AOS plugin

### Lighthouse Tests with and Without AOS

#### NO AOS Test URL
https://smg220623.dev.cogplatform.co.uk/no-aos/?Stock_ID=235371


## Lighthouse Metrics Comparison

| Metric                         | No AOS                          | With AOS                         |
|-------------------------------|----------------------------------|----------------------------------|
| **Performance Score**         | 20                               | 6                                |
| **LCP**                       | 12.6 s                           | 18.4 s                           |
| **Total Blocking Time**       | 1,300 ms                         | 2,800 ms                         |
| **Cumulative Layout Shift**   | 0.245                            | 0.467                            |
| **Speed Index**               | 9.1 s                            | 12.7 s          

#### Some Highlighted Problems from Lighthouse Report Related to AOS plugin: 

- Properly size images Potential savings of 4,413 KiB (over 4.4mb)
- Avoid enormous network payloads Total size was 39,533 KiB (over 39mb)
- Serve images in next-gen formats Potential savings of 7,988 KiB (over 7.9mb)
- Efficiently encode images Potential savings of 3,775 KiB (over 3.7mb)
- Avoid long main-thread tasks 20 long tasks found 11 tasks from AOS
- Largest Contentful Paint element 18,390 ms
    - dom element : li#aos-primary-slider-slide01.splide__slide.is-active.is-visible
    - Load Delay (83% of LCP) 15,320 ms
- Reduce the impact of third-party code Third-party code blocked the main thread for 4,180 ms (over 4.1 seconds)
  -  Biggest impact from: aos.tv blocks main thread for 2,442 ms (over 2.4 seconds)
- Reduce JavaScript execution time 5.9 s
  - Biggest impact from: aos.tv - 6.5 seconds total CPU time, 2.3 seconds script evaluation time
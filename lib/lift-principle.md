## Application Structure LIFT Principle
### LIFT
###### [Style [Y140](https://github.com/johnpapa/angular-styleguide/#style-y140)]

  - Structure your app such that you can `L`ocate your code quickly, `I`dentify the code at a glance, keep the `F`lattest structure you can, and `T`ry to stay DRY. The structure should follow these 4 basic guidelines.

    *Why LIFT?*: Provides a consistent structure that scales well, is modular, and makes it easier to increase developer efficiency by finding code quickly. Another way to check your app structure is to ask yourself: How quickly can you open and work in all of the related files for a feature?

    When I find my structure is not feeling comfortable, I go back and revisit these LIFT guidelines

    1. `L`ocating our code is easy
    2. `I`dentify code at a glance
    3. `F`lat structure as long as we can
    4. `T`ry to stay DRY (Don’t Repeat Yourself) or T-DRY

### Locate
###### [Style [Y141](https://github.com/johnpapa/angular-styleguide/#style-y141)]

  - Make locating your code intuitive, simple and fast.

    *Why?*: I find this to be super important for a project. If the team cannot find the files they need to work on quickly, they will not be able to work as efficiently as possible, and the structure needs to change. You may not know the file name or where its related files are, so putting them in the most intuitive locations and near each other saves a ton of time. A descriptive folder structure can help with this.

    ```
      /bower_components
      /src
        /app
          /components
            /basket
              basket.html
              basketController.js
              basketConstants.js
              basketDirective.js
              basketFactory.js
              basketModule.js
              basketRunBlock.js

            /hero
              hero.html
              heroController.js
              heroDirective.js
              heroModule.js
            /product
              /ebooks
                ebooksProduct.html
                ebooksProductController.js
                ebooksProductDirective.js
                ebooksProductFactory.js
                ebooksProductModule.js
              /music
                musicProduct.html
                musicProductController.js
                musicProductDirective.js
                musicProductFactory.js
                musicProductModule.js
              productFactory.js
              productModule.js
          /pages
            /landing
              /ebooks
                ebooksLandingPage.html
                ebooksLandingPageController.js
              /music
                musicLandingPage.html
                musicLandingPageController.js
            /product
              /ebooks
                ebooksProductPage.html
                ebooksProductPageController.js
              /music
                musicProductPage.html
                musicProductPageController.js
          /shared
            /filters
              someFilter.js
          appModule.js   
          appConstants.js   
          appRunBlock.js
        /toolkit
          /services
            basketRestFactory.js
            productRestFactory.js    
          toolkitModule.js   
          toolkitConstants.js   
          toolkitRunBlock.js
        index.html
    ```

### Identify
###### [Style [Y142](https://github.com/johnpapa/angular-styleguide/#style-y142)]

  - When you look at a file you should instantly know what it contains and represents.

    *Why?*: You spend less time hunting and pecking for code, and become more efficient. If this means you want longer file names, then so be it. Be descriptive with file names and keeping the contents of the file to exactly 1 component. Avoid files with multiple controllers, multiple services, or a mixture. There are deviations of the 1 per file rule when I have a set of very small features that are all related to each other, they are still easily identifiable.

### Flat
###### [Style [Y143](https://github.com/johnpapa/angular-styleguide/#style-y143)]

  - Keep a flat folder structure as long as possible. When you get to 7+ files, begin considering separation.

    *Why?*: Nobody wants to search 7 levels of folders to find a file. Think about menus on web sites … anything deeper than 2 should take serious consideration. In a folder structure there is no hard and fast number rule, but when a folder has 7-10 files, that may be time to create subfolders. Base it on your comfort level. Use a flatter structure until there is an obvious value (to help the rest of LIFT) in creating a new folder.

### T-DRY (Try to Stick to DRY)
###### [Style [Y144](https://github.com/johnpapa/angular-styleguide/#style-y144)]

  - Be DRY, but don't go nuts and sacrifice readability.

    *Why?*: Being DRY is important, but not crucial if it sacrifices the others in LIFT, which is why I call it T-DRY. I don’t want to type session-template.html for a template because, well, it’s obviously a template. If it is not obvious or by convention, then I name it.

**[Back to table of contents](../README.md/#table-of-contents)**

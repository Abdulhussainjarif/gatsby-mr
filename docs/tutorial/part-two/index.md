---
title: Introduction to Styling in Gatsby
typora-copy-images-to: ./
disableTableOfContents: true
---

<!-- Idea: Create a glossary to refer to. A lot of these terms get jumbled -->

<!--
  - Global styles
  - Component css
  - CSS-in-JS
  - CSS Modules

-->

Gatsby ट्यूटोरियलच्या भाग दोन मध्ये आपले स्वागत आहे!

## या ट्यूटोरियल मध्ये काय आहे?

या भागात आपण गॅट्सबी वेबसाइटच्या स्टाईलिंगसाठी पर्याय शोधून काढत आहात आणि साइट तयार करण्यासाठी घटकांच्या प्रतिक्रियांचा वापर करुन आणखी खोलवर जा.

## ग्लोबल स्टईल्स वापरणे

प्रत्येक साइटवर काही प्रमाणात ग्लोबल स्टईल्सी असते. यात साइटचे टायपोग्राफी आणि पार्श्वभूमी रंग यासारख्या गोष्टी समाविष्ट आहेत. या शैलींनी साइटची संपूर्ण भावना निश्चित केली आहे - भिंतीचा रंग आणि पोत जसे खोलीचा एकंदर अनुभव सेट करते.

### मानक सीएसएस फायलीसह ग्लोबल स्टईल्सी तयार करीत आहे

एखाद्या साइटवर जागतिक शैली जोडण्याचा सर्वात सोपा मार्ग म्हणजे एक ग्लोबल वापरणे `.css` स्टाईलशीट.

#### ✋ नवीन गॅटस्बी साइट तयार करा

नवीन Gatsby साइट तयार करून प्रारंभ करा. हे सर्वोत्तम असू शकते (विशेषत: जर आपण कमांड लाइनमध्ये नवीन असाल) आपण वापरलेल्या टर्मिनल विंडो बंद करण्यासाठी [part one](/tutorial/part-one/) आणि भाग दोन साठी नवीन टर्मिनल सत्र प्रारंभ करा.

एक नवीन टर्मिनल विंडो उघडा, `tutorial-part-two` नावाच्या निर्देशिकेत एक नवीन "hello world" Gatsby site तयार करा आणि नंतर या नवीन निर्देशिकेत जा:

```shell
gatsby new tutorial-part-two https://github.com/gatsbyjs/gatsby-starter-hello-world
cd tutorial-part-two
```

आपल्याकडे आता खालील संरचनेसह एक नवीन गॅटस्बी साइट (Gatsby "hello world" स्टार्टरवर आधारित) आहे:

```text
├── package.json
├── src
│   └── pages
│       └── index.js
```

#### ✋ CSS फाइलमध्ये शैली जोडा

1. आपल्या नवीन प्रकल्पात एक `.css` फाइल तयार करा:

```shell
cd src
mkdir styles
cd styles
touch global.css
```

> टीप: आपण इच्छित असल्यास आपल्या कोड संपादकाचा वापर करून या निर्देशिका आणि फायली तयार करा.

आपल्याकडे आता अशी रचना असावी:

```text
├── package.json
├── src
│   └── pages
│       └── index.js
│   └── styles
│       └── global.css
```

2. `global.css` फाईलमध्ये काही शैली परिभाषित करा:

```css:title=src/styles/global.css
html {
  background-color: lavenderblush;
}
```

> टीप: `/src/styles/` फोल्डरमध्ये उदाहरणार्थ CSS फाईलची प्लेसमेंट अनियंत्रित आहे

#### ✋ `Gatsby-browser.js` मध्ये स्टाईलशीट समाविष्ट करा

1. Create the `gatsby-browser.js`

```shell
cd ../..
touch gatsby-browser.js
```

आपल्या प्रोजेक्टची फाईल स्ट्रक्चर आता यासारखी दिसली पाहिजे:

```text
├── package.json
├── src
│   └── pages
│       └── index.js
│   └── styles
│       └── global.css
├── gatsby-browser.js
```

> 💡 `Gatsby-browser.js` म्हणजे काय? या बद्दल जास्त काळजी करू नका आणि आत्ताच, हे जाणून घ्या की `gatsby-browser.js` ही मूठभर खास फायलींपैकी एक आहे जी गॅटस्बी शोधते आणि वापरते (त्या अस्तित्वात असल्यास). येथे ** फाईलचे नाव देणे ** महत्वाचे आहे. आपण आता अधिक एक्सप्लोर करू इच्छित असल्यास, [the docs](/docs/browser-apis/) पहा.

2. आपली अलीकडे-निर्मित शैली पत्रक `gatsby-browser.js` फायलीमध्ये आयात करा:

```javascript:title=gatsby-browser.js
import "./src/styles/global.css"

// or:
// require('./src/styles/global.css')
```

> टीप: दोन्ही कॉमनजेएस (`require`) आणि ईएस मॉड्यूल (`import`) सिंटॅक्स येथे कार्य करतात. आपल्याला काय निवडायचे याची आपल्याला खात्री नसल्यास, `import` एक चांगला डीफॉल्ट असतो. तथापि केवळ Node.js वातावरणात चालणार्‍या फायलींसह कार्य करताना (जसे की `gatsby-node.js`), `require` वापरणे आवश्यक आहे.

3. विकास सर्व्हर प्रारंभ करा:

```shell
gatsby develop
```

आपण ब्राउझरमधील आपल्या प्रोजेक्टवर नजर टाकल्यास आपण "hello world" स्टार्टरवर लागू केलेली लैव्हेंडर पार्श्वभूमी पहावी:

![Lavender Hello World!](global-css.png)

>टीपः ट्यूटोरियलच्या या भागामध्ये ats `gatsby-browser.js` वापरुन मानक सीएसएस फायली थेट आयात करणे - गॅटस्बी साइटचे स्टाईलिंग प्रारंभ करण्याच्या जलद आणि सोप्या मार्गावर लक्ष केंद्रित केले आहे. बहुतांश घटनांमध्ये, जागतिक शैली जोडण्याचा सर्वोत्तम मार्ग म्हणजे सामायिक केलेल्या लेआउट घटकासह. [Check out the docs](/docs/global-css/) त्या दृष्टीकोनाबद्दल अधिक जाणून घ्या.

## घटक-स्कोप्ड CSS वापरणे

आतापर्यंत आम्ही मानक CSS स्टाईलशीट वापरण्याच्या अधिक पारंपारिक दृष्टिकोनाबद्दल बोललो आहोत. आता घटक-अभिमुख मार्गाने स्टाईल हाताळण्यासाठी CSS मॉड्युलायझिंग करण्याच्या विविध पद्धतींबद्दल आपण बोलू.

### CSS मॉड्यूल

चला ** CSS मॉड्यूल ** एक्सप्लोर करूया. पासून उद्धृत
[the CSS Module homepage](https://github.com/css-modules/css-modules):

> ए ** CSS मॉड्यूल ** ही एक सीएसएस फाईल आहे ज्यात सर्व वर्गांची नावे आणि अ‍ॅनिमेशन नावे आहेत
> डीफॉल्टनुसार स्थानिक पातळीवर स्कोप केलेले आहेत.

CSS मॉड्यूल खूप लोकप्रिय आहेत कारण ते आपल्याला सामान्यपणे CSS लिहू देतात परंतु बर्‍याच सुरक्षिततेसह. साधन स्वयंचलितपणे अद्वितीय वर्ग आणि अ‍ॅनिमेशन नावे व्युत्पन्न करते, म्हणून आपल्याला निवडकर्त्याच्या नावाच्या टक्करांची चिंता करण्याची आवश्यकता नाही.

Gatsby CSS मॉड्यूलसह बॉक्सच्या बाहेर कार्य करते. Gatsby (आणि सर्वसाधारणपणे प्रतिक्रिया द्या) सह नवीन बांधकाम करणार्‍यांसाठी हा दृष्टिकोन अत्यंत शिफारसीय आहे.

#### ✋ CSS मॉड्यूल्स वापरुन एक नवीन पृष्ठ तयार करा

यया विभागात, आपण एक नवीन पृष्ठ घटक तयार करा आणि CSS मॉड्यूल वापरुन पृष्ठ घटक शैली बनवाल.

प्रथम, नवीन `Container` घटक तयार करा.

1. `src/components` वर एक नवीन निर्देशिका तयार करा आणि नंतर या नवीन निर्देशिकेत `container.js` नावाची फाईल तयार करा आणि पुढील पेस्ट करा:

```jsx:title=src/components/container.js
import React from "react"
import containerStyles from "./container.module.css"

export default ({ children }) => (
  <div className={containerStyles.container}>{children}</div>
)
```

आपण `container.module.css` नावाची CSS मॉड्यूल फाइल आयात केल्याचे आपल्या लक्षात येईल. आता ती फाईल बनवू.

2. त्याच निर्देशिकेत (`src/components`), एक `container.module.css` फाइल तयार करा आणि खालील कॉपी / पेस्ट करा:

```css:title=src/components/container.module.css
.container {
  margin: 3rem auto;
  max-width: 600px;
}
```

आपल्या लक्षात येईल की फाईलचे नाव सामान्य `.css` ऐवजी` .module.css` ने समाप्त होईल. हे आपण गॅट्सबाईला कसे सांगता की या CSS फाईलवर साध्या CSS ऐवजी CSS विभाग म्हणून प्रक्रिया केली जावी.

3. येथे फाइल तयार करून नवीन पृष्ठ घटक तयार करा
   `src/pages/about-css-modules.js`:

```jsx:title=src/pages/about-css-modules.js
import React from "react"

import Container from "../components/container"

export default () => (
  <Container>
    <h1>About CSS Modules</h1>
    <p>CSS Modules are cool</p>
  </Container>
)
```

आता आपण `http://localhost:8000/about-css-modules/` visit ला भेट दिल्यास, आपले पृष्ठ यासारखे काहीतरी दिसावे:

![Page with CSS module styles](css-modules-basic.png)

#### ✋ CSS मॉड्यूल्स वापरुन घटकाची शैली बनवा

या विभागात आपण नावे, अवतार आणि लघु लॅटिन चरित्रे असलेल्या लोकांची सूची तयार कराल. आपण एक CSS मॉड्यूल वापरुन तो घटक आणि शैली'll `<User />` create तयार कराल.

1. CSS साठी फाइल `src/pages/about-css-modules.module.css` वर तयार करा.

2. नवीन फाईलमध्ये पुढील पेस्ट करा:

```css:title=src/pages/about-css-modules.module.css
.user {
  display: flex;
  align-items: center;
  margin: 0 auto 12px auto;
}

.user:last-child {
  margin-bottom: 0;
}

.avatar {
  flex: 0 0 96px;
  width: 96px;
  height: 96px;
  margin: 0;
}

.description {
  flex: 1;
  margin-left: 18px;
  padding: 12px;
}

.username {
  margin: 0 0 12px 0;
  padding: 0;
}

.excerpt {
  margin: 0;
}
```

3. यापूर्वी फाईलच्या पहिल्या काही ओळींमध्ये संपादन करून तुम्ही तयार केलेल्या `about-css-modules.js` पृष्ठामध्ये नवीन `src/pages/about-css-modules.module.css` फाईल आयात करा.

```javascript:title=src/pages/about-css-modules.js
import React from "react"
// highlight-next-line
import styles from "./about-css-modules.module.css"
import Container from "../components/container"

// highlight-next-line
console.log(styles)
```

`console.log(styles)` कोड परिणामी आयटमवर लॉग इन करेल जेणेकरून आपण आपल्या प्रक्रिया केलेल्या `./about-css-modules.module.css` फाइलचा परिणाम पाहू शकाल. आपण आपल्या ब्राउझरमध्ये विकसक कन्सोल (उदा. फायरफॉक्स किंवा क्रोमच्या विकसक साधनांचा वापर करून, बहुधा F12 की द्वारे) उघडल्यास आपण दिसेल:

![Import result of CSS module in console](css-modules-console.png)

आपण याची तुलना आपल्या CSS फाईलशी केल्यास, आपल्याला दिसेल की प्रत्येक वर्ग आता आयात केलेल्या ऑब्जेक्टमध्ये एक लांब स्ट्रिंगकडे निर्देशित केलेली उदा. `avatar` पॉइंट्स `src-pages----about-css-modules-module---avatar---2lRF7`. CSS मॉड्यूल व्युत्पन्न केलेली ही नावे आहेत. आपल्या साइटवर ते अद्वितीय असल्याची हमी दिलेली आहे. आणि आपल्याला वर्ग वापरण्यासाठी त्यांना आयात करावे लागत असल्याने काही CSS कोठे वापरल्या जातील याचा प्रश्न उद्भवत नाही.

4. `about-css-modules.js` पृष्ठामध्ये नवीन `<User />` घटक इनलाइन तयार करा
    घटक. `about-css-modules.js` सुधारित करा जेणेकरून ते पुढीलप्रमाणे दिसते:

```jsx:title=src/pages/about-css-modules.js
import React from "react"
import styles from "./about-css-modules.module.css"
import Container from "../components/container"

console.log(styles)

// highlight-start
const User = props => (
  <div className={styles.user}>
    <img src={props.avatar} className={styles.avatar} alt="" />
    <div className={styles.description}>
      <h2 className={styles.username}>{props.username}</h2>
      <p className={styles.excerpt}>{props.excerpt}</p>
    </div>
  </div>
)
// highlight-end

export default () => (
  <Container>
    <h1>About CSS Modules</h1>
    <p>CSS Modules are cool</p>
    {/* highlight-start */}
    <User
      username="Jane Doe"
      avatar="https://s3.amazonaws.com/uifaces/faces/twitter/adellecharles/128.jpg"
      excerpt="I'm Jane Doe. Lorem ipsum dolor sit amet, consectetur adipisicing elit."
    />
    <User
      username="Bob Smith"
      avatar="https://s3.amazonaws.com/uifaces/faces/twitter/vladarbatov/128.jpg"
      excerpt="I'm Bob Smith, a vertically aligned type of guy. Lorem ipsum dolor sit amet, consectetur adipisicing elit."
    />
    {/* highlight-end */}
  </Container>
)
```

> टीपः साधारणपणे, आपण एखाद्या साइटवरील एकाधिक ठिकाणी घटक वापरत असल्यास, ते its `components`  निर्देशिकेतील त्याच्या स्वतःच्या मॉड्यूल फाइलमध्ये असावे. परंतु, जर तो फक्त एका फाईलमध्ये वापरला असेल तर तो इनलाइन तयार करा.

तयार झालेले पृष्ठ आता यासारखे दिसले पाहिजे:

![User list page with CSS modules](css-modules-userlist.png)

### CSS-in-JS

CSS-in-JS हा घटक-आधारित स्टाईल दृष्टीकोन आहे. सामान्यत :, हा एक नमुना आहे जेथे जावास्क्रिप्ट वापरुन [CSS is composed inline using JavaScript](https://reactjs.org/docs/faq-styling.html#what-is-css-in-js).

#### Gatsby सह CSS-in-JS वापरणे

CSS-in-JS लायब्ररी बरेच भिन्न आहेत आणि त्यापैकी बर्‍याच जणांकडे आधीपासून Gatsby प्लगइन आहेत. आम्ही या आरंभिक ट्यूटोरियलमध्ये CSS-in-JS उदाहरण समाविष्ट करणार नाही, परंतु पर्यावरणशास्त्र आपल्याला काय देऊ करेल हे [explore](/docs/styling/) करण्यास आम्ही प्रोत्साहित करतो. दोन लायब्ररीत विशेषत: [Emotion](/docs/emotion/)  आणि  [Styled Components](/docs/styled-components/) साठी मिनी-ट्यूटोरियल आहेत.

#### CSS-in-JS वर वाचन सुचविले

आपल्याला पुढील वाचनामध्ये स्वारस्य असल्यास, [Christopher "vjeux" Chedeau's 2014 presentation that sparked this movement](https://speakerdeck.com/vjeux/react-css-in-js) तसेच [Mark Dalgleish's more recent post "A Unified Styling Language"](https://medium.com/seek-blog/a-unified-styling-language-d0c208de2660).

### इतर CSS पर्याय

गॅटस्बी जवळजवळ प्रत्येक संभाव्य स्टाईलिंग पर्यायांना समर्थन देते (आपल्या पसंतीच्या सीएसएस पर्यायासाठी अद्याप प्लगइन नसल्यास, [कृपया एकाचे योगदान द्या!](/contributing/how-to-contribute/))

- [Typography.js](/packages/gatsby-plugin-typography/)
- [Sass](/packages/gatsby-plugin-sass/)
- [JSS](/packages/gatsby-plugin-jss/)
- [Stylus](/packages/gatsby-plugin-stylus/)
- [PostCSS](/packages/gatsby-plugin-postcss/)

आणि अधिक!

## पुढे काय येत आहे?

आता [part three of the tutorial](/tutorial/part-three/) वर जा, जिथे आपण Gatsby प्लगइन आणि लेआउट घटकांबद्दल शिकू शकाल.

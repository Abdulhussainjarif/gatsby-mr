---
title: Source Plugins
typora-copy-images-to: ./
disableTableOfContents: true
---

> हे ट्यूटोरियल Gatsby’s डेटा लेयर बद्दलच्या मालिकेचा एक भाग आहे. आपण जात असल्याचे सुनिश्चित करा [part 4](/tutorial/part-four/) येथे सुरू ठेवण्यापूर्वी.

## या ट्यूटोरियल मध्ये काय आहे?

या ट्यूटोरियल मध्ये, आपण GraphQL आणि स्त्रोत प्लगइन वापरुन आपल्या गॅटस्बी साइटमध्ये डेटा कसा काढायचा याबद्दल शिकत आहात. तथापि आपण या प्लगइन्सबद्दल जाणून घेण्यापूर्वी, आपल्याला GraphiQL नावाचे काहीतरी कसे वापरावे हे जाणून घ्यायचे आहे, एक साधन जे आपणास आपल्या क्वेरीची योग्यरित्या रचना करण्यात मदत करते.

## सादर करीत आहोत GraphiQL

GraphiQL म्हणजे GraphQl ग्इंटिग्रेटेड डेव्हलपमेंट एंवीरोन्मेन्ट (आयडीई). हे एक शक्तिशाली (आणि सर्वत्र अद्भुत) साधन आहे जे आपण गॅटस्बी वेबसाइट्स तयार करताना वारंवार वापरता.

जेव्हा आपल्या साइटचा डेव्हलपमेंट सर्व्हर चालू असतो तेव्हा आपण त्यात प्रवेश करू शकता - सामान्यपणे

`http://localhost:8000/___graphql`.

<video controls="controls" autoplay="true" loop="true">
  <source type="video/mp4" src="/graphiql-explore.mp4" />
  <p>आपला ब्राउझर व्हिडिओ घटकास समर्थन देत नाही.</p>
</video>

अंगभूत सुमारे झोके `Site` "प्रकार" आणि त्यावर कोणती फील्ड उपलब्ध आहेत ते पहा `siteMetadata` ऑब्जेक्ट आपण आधी चौकशी केली. GraphiQL आणि उघडण्याचा प्रयत्न करा आपल्या डेटासह खेळा! दाबा <kbd>Ctrl + Space</kbd> (किंवा वापरा <kbd>Shift + Space</kbd> वैकल्पिक कीबोर्ड शॉर्टकट म्हणून) स्वयंपूर्ण विंडो आणण्यासाठी आणि <kbd>Ctrl + Enter</kbd> GraphQL क्वेरी चालवण्यासाठी. ट्युटोरियलच्या उर्वरित भागातून आपण आणखी बरेच काही GraphiQL वापरणार आहात.

## GraphiQL एक्सप्लोरर वापरणे

ग्रॅफिक्यूएल एक्सप्लोरर आपल्याला या शेअर्स हाताने पुन्हा पुन्हा पुन्हा टाइप करण्याच्या प्रक्रियेशिवाय उपलब्ध फील्ड्स आणि इनपुटवर क्लिक करून परस्पर संवाद साधण्यास सक्षम करते.

<EggheadEmbed
  lessonLink="https://egghead.io/lessons/gatsby-build-a-graphql-query-using-gatsby-s-graphiql-explorer"
  lessonTitle="Build a GraphQL Query using Gatsby’s GraphiQL Explorer"
/>

## स्त्रोत प्लगइन

गॅटस्बी साइट मधील डेटा कोठूनही येऊ शकतोः एपीआय, डेटाबेस, सीएमएस, स्थानिक फायली इ.

स्त्रोत प्लगइन त्यांच्या स्त्रोतांमधून डेटा आणतात. उदा. फाइल सिस्टम स्रोत प्लगइनला फाइल सिस्टममधून डेटा कसा आणला जावा हे माहित असते. वर्डप्रेस प्लगइनला वर्डप्रेस एपीआय वरून डेटा कसा आणता येईल हे माहित आहे.

जोडा [`gatsby-source-filesystem`](/packages/gatsby-source-filesystem/) आणि ते कसे कार्य करते ते एक्सप्लोर करा.

प्रथम, प्रकल्पाच्या मुळाशी प्लगइन इन्स्टॉल करा.

```shell
npm install --save gatsby-source-filesystem
```

मग ते आपल्या `gatsby-config.js`मध्ये ऍड करा :

```javascript:title=gatsby-config.js
module.exports = {
  siteMetadata: {
    title: `Pandas Eating Lots`,
  },
  plugins: [
    // highlight-start
    {
      resolve: `gatsby-source-filesystem`,
      options: {
        name: `src`,
        path: `${__dirname}/src/`,
      },
    },
    // highlight-end
    `gatsby-plugin-emotion`,
    {
      resolve: `gatsby-plugin-typography`,
      options: {
        pathToConfigModule: `src/utils/typography`,
      },
    },
  ],
}
```

ते सेव्ह करा आणि गॅट्सबी डेव्हलपमेंट सर्व्हर रीस्टार्ट करा. मग पुन्हा ग्रॅफिक्यूएल उघडा.

एक्सप्लोरर पेन, आपण पहाल `allFile` आणि `file` निवडी म्हणून उपलब्ध:

![graphiql-filesystem](graphiql-filesystem.png)

क्लिक करा `allFile` ड्रॉपडाउन. नंतर आपला कर्सर ठेवा `allFile` क्वेरी क्षेत्रात आणि नंतर टाइप करा <kbd>Ctrl + Enter</kbd>. हे यासाठी क्वेरी पूर्व-भरेल`id` प्रत्येक फाईलचा.क्वेरी चालविण्यासाठी "प्ले" दाबा:

![filesystem-query](filesystem-query.png)

एक्सप्लोरर उपखंडात, `id` फील्ड स्वयंचलितपणे निवडले गेले आहे. फील्डचा संबंधित चेकबॉक्स तपासून अधिक फील्डसाठी निवडी करा. नवीन फील्डसह क्वेरी पुन्हा चालविण्यासाठी "प्ले" दाबा:

![filesystem-explorer-options](filesystem-explorer-options.png)

वैकल्पिकरित्या, आपण स्वयंपूर्ण शॉर्टकट वापरुन फील्ड जोडू शकता(<kbd>Ctrl + Space</kbd>). हे वर क्वेरीयोग्य फील्ड दर्शवेल `File` नोड्स.

![filesystem-autocomplete](filesystem-autocomplete.png)

आपल्या क्वेरीवर अनेक फील्ड जोडण्याचा प्रयत्न करा, दाबा <kbd>Ctrl + Enter</kbd>
क्वेरी पुन्हा चालविण्यासाठी प्रत्येक वेळी. आपण अद्यतनित क्वेरी परिणाम दिसेल:

![allfile-query](allfile-query.png)

याचा परिणाम अ‍ॅरे आहे `File` "नोड्स" (नोड ए मधील ऑब्जेक्टसाठी एक काल्पनिक नाव आहे
"आलेख"). प्रत्येक `File` नोड ऑब्जेक्टमध्ये आपण फिल्डसाठी क्वेरी केली आहे.

## GraphQL क्वेरीसह एक पेज तयार करा

गॅटस्बी सह नवीन पृष्ठे तयार करणे बर्‍याचदा ग्राफिक्यूएलमध्ये सुरू होते. आपण प्रथम रेखाटन करा
ग्रॅफिक्यूएल मध्ये प्ले करून डेटा क्वेरी नंतर त्यास प्रतिक्रिया पृष्ठ घटकावर कॉपी करा
UI तयार करणे सुरू करण्यासाठी

चला हे करून पाहू.

येथे एक नवीन फाईल तयार करा `src/pages/my-files.js` सह `allFile` आपण आत्ताच तयार केलेला ग्राफिक क्वेरी:


```jsx:title=src/pages/my-files.js
import React from "react"
import { graphql } from "gatsby"
import Layout from "../components/layout"

export default ({ data }) => {
  console.log(data) // highlight-line
  return (
    <Layout>
      <div>Hello world</div>
    </Layout>
  )
}

export const query = graphql`
  query {
    allFile {
      edges {
        node {
          relativePath
          prettySize
          extension
          birthTime(fromNow: true)
        }
      }
    }
  }
`
```

द `console.log(data)` ओळ वर ठळक केली आहे. हे सहसा उपयुक्त ठरते तेव्हा
आपण GraphQL क्वेरीमधून प्राप्त करीत असलेल्या डेटाचे सांत्वन करण्यासाठी एक नवीन घटक तयार करणे
जेणेकरून आपण यूआय तयार करताना आपल्या ब्राउझर कन्सोलमधील डेटा एक्सप्लोर करू शकता.

आपण नवीन पेज भेट दिली तर `/my-files/` आणि आपला ब्राउझर कन्सोल उघडा आपल्याला असे काहीतरी दिसेल:

![data-in-console](data-in-console.png)

डेटाचा आकार GraphQL क्वेरीच्या आकाराशी जुळतो.

फाईल डेटा प्रिंट करण्यासाठी आपल्या घटकामध्ये काही कोड जोडा.

```jsx:title=src/pages/my-files.js
import React from "react"
import { graphql } from "gatsby"
import Layout from "../components/layout"

export default ({ data }) => {
  console.log(data)
  return (
    <Layout>
      {/* highlight-start */}
      <div>
        <h1>My Site's Files</h1>
        <table>
          <thead>
            <tr>
              <th>relativePath</th>
              <th>prettySize</th>
              <th>extension</th>
              <th>birthTime</th>
            </tr>
          </thead>
          <tbody>
            {data.allFile.edges.map(({ node }, index) => (
              <tr key={index}>
                <td>{node.relativePath}</td>
                <td>{node.prettySize}</td>
                <td>{node.extension}</td>
                <td>{node.birthTime}</td>
              </tr>
            ))}
          </tbody>
        </table>
      </div>
      {/* highlight-end */}
    </Layout>
  )
}

export const query = graphql`
  query {
    allFile {
      edges {
        node {
          relativePath
          prettySize
          extension
          birthTime(fromNow: true)
        }
      }
    }
  }
`
```

आणि आता भेट द्या `http://localhost:8000/my-files`… 😲

![my-files-page](my-files-page.png)

## पुढे काय येत आहे?

स्त्रोत प्लगइन _into_ Gatsby च्या डेटा सिस्टममध्ये डेटा कसा आणतात हे आता आपण शिकलात. पुढील ट्यूटोरियल मध्ये, आपण स्रोत प्लगइनद्वारे आणलेली कच्ची सामग्री ट्रान्सफॉर्मर प्लगइन _ट्रान्सफॉर्म_ कसे करावे हे शिकू शकाल. सोर्स प्लगइन्स आणि ट्रान्सफॉर्मर प्लगइन यांचे संयोजन गॅटस्बी साइट तयार करताना आपल्याला आवश्यक असलेले सर्व डेटा सोर्सिंग आणि डेटा ट्रान्सफॉर्मेशन हाताळू शकते. मध्ये ट्रान्सफॉर्मर प्लगइन बद्दल जाणून घ्या [part six of the tutorial](/tutorial/part-six/).

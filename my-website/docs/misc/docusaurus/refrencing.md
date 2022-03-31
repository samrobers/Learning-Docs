I am referencing a [document](doc2.md).

Reference to another [document in a subfolder](subfolder/doc3.md).

[Relative document](../otherFolder/doc4.md) referencing works as well.

Inline SVGs
Docusaurus supports inlining SVGs out of the box.

```
import DocusaurusSvg from './docusaurus.svg';


[data-theme='dark'] .themedDocusaurus [fill='#FFFF50'] {
  fill: seagreen;
}
<DocusaurusSvg />;
```

Files
In the same way, you can link to existing assets by require'ing them and using the returned URL in videos, a anchor links, etc.

```
# My Markdown page

<a target="\_blank" href={require('./assets/docusaurus-asset-example.docx').default}> Download this docx </a>

or

[Download this docx using Markdown](./assets/docusaurus-asset-example.docx)
```

```
<img
  src={require('./assets/docusaurus-asset-example-banner.png').default}
  alt="Example banner"
/>


import myImageUrl from './assets/docusaurus-asset-example-banner.png';

<img src={myImageUrl} alt="Example banner" />;



![Example banner](./assets/docusaurus-asset-example-banner.png)

```

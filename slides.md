---
theme: seriph
background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## Atomic design system
  Better system for creating better websites
  About methodology and why we should use it!
title: Atomic design system
---

# Atomic design system

Better system for creating better websites

About methodology and why we should use it!

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

# What is atomic design?

Atomic design is methodology for creating design systems. There are five distinct levels in atomic design:

<img src="https://cdn-images-1.medium.com/fit/t/1600/480/1*GFkjjKLjnhOSLn-kM8jB8Q.png" alt="atomic design graph">

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

<style>
</style>


---

# Atoms

#### Atoms are the basic building blocks of matter.
Applied to web interfaces, atoms are our HTML tags, such as a form label, an input or a button.

<img src="https://bradfrost.com/wp-content/uploads/2013/06/atoms.jpg"/>

<style>
  img {
  	height: 350px;
    margin: 0 auto;
  }
</style>


---

# Molecules

#### Things start getting more interesting and tangible when we start combining atoms together.
Molecules are groups of atoms bonded together and are the smallest fundamental units of a compound.
These molecules take on their own properties and serve as the backbone of our design systems.

Building up to molecules from atoms encourages a “do one thing and do it well” mentality.
While molecules can be complex, as a rule of thumb they are relatively simple combinations of atoms built for reuse.

<img src="https://bradfrost.com/wp-content/uploads/2013/06/molecule.jpg"/>

<style>
  img {
    height: 120px;
    object-fit: cover;
    margin: 0 auto;
    width: 400px;
  }
</style>

---

# Organisms

#### Molecules give us some building blocks to work with, and we can now combine them together to form organisms. Organisms are groups of molecules joined together to form a relatively complex, distinct section of an interface.

We’re starting to get increasingly concrete. A client might not be terribly interested in the molecules of a design system, but with organisms we can see the final interface beginning to take shape.

<img src="https://bradfrost.com/wp-content/uploads/2013/06/organism2.jpg"/>

<style>
  img {
    height: 90px;
    object-fit: cover;
    margin: 0 auto;
    width: 1000px;
  }
</style>

---

# Templates

#### At the template stage, we break our chemistry analogy to get into language that makes more sense to our clients and our final output. Templates consist mostly of groups of organisms stitched together to form pages. It’s here where we start to see the design coming together and start seeing things like layout in action.

<img src="https://bradfrost.com/wp-content/uploads/2013/06/template1.jpg"/>

<style>
  img {
    height: 350px;
    object-fit: contain;
    margin: 20px auto 0;
    width: 1000px;
  }
</style>

---

# Pages

#### Pages are specific instances of templates. Here, placeholder content is replaced with real representative content to give an accurate depiction of what a user will ultimately see.

<img src="https://bradfrost.com/wp-content/uploads/2013/06/page1.jpg"/>

<style>
  img {
    height: 350px;
    object-fit: contain;
    margin: 20px auto 0;
    width: 1000px;
  }
</style>


---
layout: image-right
image: https://source.unsplash.com/collection/94734567/1920x1080
---

# Code - atom

```ts
import styled from '@emotion/styled'

const StyledInput = styled('input')`
  color: grey;
  font-size: 16px;
  font-family: inherit;
`

export default StyledInput
```

```ts
import styled from '@emotion/styled'

const Text = styled('p')`
  color: black;
  font-size: 16px;
`

export default Text
```

---
layout: image-right
image: https://source.unsplash.com/collection/94734568/1920x1080
---

# Code - molecule

```tsx
import styled from '@emotion/styled'
import Text from '../atoms/Text'
import StyledInput from '../atoms/StyledInput'

const TextInput = ({text, ...props}: ITextInput) => (
  <div>
    <Text>{props.text}</Text>
    <StyledInput {...props} />
  </div>
)

export default TextInput
```

---
layout: image-right
image: https://source.unsplash.com/collection/94734569/1920x1080
---

# Code - organism

```tsx
import {Controller} from 'react-hook-form'
import TextInput from '../molecules/TextInput'
// ...
const TextInputQuestion = (props: ITextInputQuestion) => (
  <FancyContainer>
    <Controller
      control={props.control}
      name={props.name}
      defaultValue={''}
      render={(renderProps, inputProps) => {
        // Maybe magic ✨ here? Who knows!
        // Possibilities are endless!
        return (
          <FileInput
            {...renderProps}
            {...inputProps}
            {...props}
          />
        );
      }}
    />
    <FancyHr/>
  </FancyContainer>
)

export default TextInputQuestion
```

---
layout: image-right
image: https://source.unsplash.com/collection/94734570/1920x1080
---

# Code - template

```tsx
import Header1 from '../molecules/Header1'
import TextInputQuestion from '../organisms/TextInputQuestion'

const HomePageView = (props: IHomePageView) => (
  <Container>
    <form onSubmit={props.form.handleSubmit(props.onSubmit)}>
      <Header1>My super form!</Header1>
      <TextInputQuestion
        control={props.form.control}
        name='firstName'
        title='Please enter your first name'
      />
      <TextInputQuestion
        control={props.form.control}
        name='lastName'
        title='Please enter your last name'
      />
      <button type='submit'>Submit</button>
    </form>
  </Container>
)

export default TextInputQuestion
```

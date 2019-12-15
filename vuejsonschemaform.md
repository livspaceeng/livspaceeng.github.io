# VueJSONSchemaForm (0.1.6)

A vuejs component for rendering JSON Schema as forms.

# Quick Start

You will need a vuejs project to use this component. You can create a new project if you dont have one using [@vue/cli](https://cli.vuejs.org/).

## Installation

You must have access to the private [npm registry](http://www.google.com) of livspace to download this package.

```bash
  npm i --save @canvas/vuejsonschemaform
```

## Usage

If you have a webpack project already setup you can now import and use the component.

__Template section__
```html
<div>
  <Form
    :layout="'horizontal'"
    :schema="formstructure"
    :renderers="renderers"
    :initialData="initialdata"
    ref="form"
  />
</div>
```

__Script section__
```javascript
import { Form, CustomRenderers } from '@canvas/vuejsonschemaform';
export default Vue.extend({
  data() {
    return {
      schema: {},
      initialdata: null
    }
  },
  components: {
    Form
  },
  mounted() {
    this.schema = {
      title: 'Form',
      type: 'object',
      properties: {
        username: {
          type: 'string',
          title: 'User Name'
        }
      }
    };
  },
  computed: {
    renderers() {
      return CustomRenderers;
    },
    formstructure() {
      return this.schema;
    },
  }
})
```

__Style section__
```css
@import url('../../node_modules/@canvas/vuejsonschemaform/dist/vuejsonschemaform.css');
```
If you are using typescript, you may get an error saying `Could not find a declaration file for module '@canvas/vuejsonschemaform'...`. At this time we do not have a type
declaration file available for vuejsonschemaform. So, just create a file named
`vuejsonschemaform.d.ts` in the src folder and add the line
`declare module '@canvas/vuejsonschemaform';` in it. A declaration file will be
published soon to fix this issue.

# Conditional rendering
You can handle conditional showing hiding of form elements using the conditional
schema constructs of JSONSchema 7 specification.

# Custom renderers
The component renders the schema recursively. At each call control is passed to
a renderer and then back to the caller. You can introduce your own renderers in
case you want to use this to render your components.

If you are using canvas components you should share the renderers that are available
or contribute the components library. Do not add your component in your own project
alone to ensure continued support and upgrades.

If its your own project then make sure you use css modules so that no changes on
our side can affect your components.

To write a custom renderer do the following:
```typescript
// Your renderer.tsx
function renderMyComponent(this: From, ) {

}
```

# Leveraging tree transformers (coming soon)
You can get transform data in one json object to another using the schema as a key.
To do this you must use the following functions.

# Available renderers
The library provides some renderers packed in. Some of them are not fully controlled
by the schema. Note that if you write any custom components then you will be
modifying the schema to suit your needs. Such small modifications are documented here:

## Date picker

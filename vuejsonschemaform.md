# vuejsonschemaform

A vuejs component for rendering [JSON Schema](https://json-schema.org/draft-07/json-schema-release-notes.html) as forms.
The latest version available for use is 0.1.6.

# Installation

You must have access to the private [npm registry](http://www.google.com) of livspace to download this package.

```bash
  npm i @canvas/vuejsonschemaform
```

# Usage
You have to use it just like any other vuejs component:
```
  <div>
    <Form
      :schema="someschema"
      ref="form"
    />
    <button @click="handleSubmit">
      Submit
    </button>
  </div>
```
```typescript
Vue.extend({
  methods: {
    handleSubmit(arg) {
      const data = this.$refs.form.getData();
      if (data) {
        fetch('/endpoint', data);
      }
    }
  }
})
```

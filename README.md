# \<test-element\>



## Install the Polymer-CLI

First, make sure you have the [Polymer CLI](https://www.npmjs.com/package/polymer-cli) installed. Then run `polymer serve` to serve your element locally.

## Viewing Your Element

```
$ polymer serve
```

## Running Tests

```
$ polymer test
```

Your application is already set up to be tested via [web-component-tester](https://github.com/Polymer/web-component-tester). Run `polymer test` to run your application's test suite locally.
# testelement

## Writing our first test
### Add the test fixture to the body of the test file
```
<test-fixture id="BasicTestFixture">
    <template>
        <custom-element ></custom-element>
    </template>
</test-fixture>
```
### Add the tests themselves to the body of the file

```
<script>
    suite('custom-element', function() {

        test('instantiating the element with default properties works', function() {
            var element = fixture('BasicTestFixture');
            assert.equal(element.textContent, 'I\'m a custom-element.');
            assert.equal(element.prop1, 'custom-element-prop1');
        });

    });
</script>
```
### Here is the custom-element implementation which will make that test pass
```
<link rel="import"  href="https://polygit.org/components/polymer/polymer-element.html">

<script>
    // Define the class for a new element called custom-element
    class CustomElement extends Polymer.Element {
        static get is() { return "custom-element"; }
        constructor() {
            super();
            this.textContent = "I'm a custom-element.";
         //   this.prop1 = "yo"
        }

        static get properties() {
            return {
                prop1: {
                    type: String,
                    value: 'custom-element-prop1'
                }
            };
        }
    }
    // Register the new element with the browser
    customElements.define(CustomElement.is, CustomElement);
</script>

```


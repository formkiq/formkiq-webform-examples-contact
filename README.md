
# FormKiQ Webform Examples - Contact Form
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Using [FormKiQ Core](https://github.com/formkiq/formkiq-core), you can handle web forms on your site in minutes.**

This example uses the FormKiQ Client JavaScript SDK: https://www.npmjs.com/package/formkiq-client-sdk-javascript

# Auto-Wired Forms

The FormKiQ Client JavaScript SDK includes an optional auto-wiring function. In order to have your form automatically submit to your FormKiQ Core deployment, you can add a className of "fkq-form" to your &lt;form&gt; element. 

**NOTE: Validation has not yet been implemented for auto-wired forms.**

# Submitting a Form Manually

If you would rather handle the form manually, you can use the FormKiQ Client SDK to access the FormKiQ Core API. You will still receive the same onFormSubmitted and onFormCompleted events.

## Example

```html
<form name="Contact Form" onsubmit="submitForm(this);return false;">
    [...]
</form>

<script>
    let formkiqClient;

    window.onload = () => {
        formkiqClient = new FormkiqClient('{FormkiqHttpApiUrl}');
    }

    function submitForm(thisForm) {

        // TODO: validation

        formkiqClient.webFormsHandler.submitFormkiqForm(thisForm);
    }

    function onFormSubmitted(formName) {
        console.log(`${formName} has been submitted for processing.`);
    }

    [...]

</script>
```

# The Form Element Name Attribute

By default, the name of your form will also be submitted as a Tag to FormKiQ Core, to help differentiate if you have multiple web forms set up to submit to FormKiQ.

# File Attachments

This contact form example is simple by design. To work with file attachments, we have created another example for reference: a [Job Application Form](https://github.com/formkiq/formkiq-webform-examples-jobapplication).

# Customizing the data sent to FormKiQ Core

Rather than using the WebFormHandler that comes with the FormKiQ Client SDK, you can create your own data parameters to send directly to the FormKiQ Public POST /documents Endpoint.

NOTE: only the Public POST /documents Endpoint should be used, as you do not want to expose your FormKiQ Core authentication credentials in client-side code.

# Try It Out

Once you have added your FormKiQ Core HTTP API URL (see the inline comments in index.html for more info), you can test this FormKiQ Web Form out by running http-server:
```sh
npx http-server
```

![Screenshot of Contact Form Example](https://raw.githubusercontent.com/formkiq/formkiq-webform-examples-contact/master/screenshot.png)

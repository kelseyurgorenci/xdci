---
title: 'Get Started'
form:
    name: contact-form
    fields:
        -
            name: name
            label: Name
            placeholder: Name
            autofocus: 'on'
            autocomplete: 'on'
            type: text
            validate:
                required: true
        -
            name: email
            label: Email
            placeholder: Email
            type: email
            validate:
                required: true
        -
            name: department
            label: 'Department and/or Institution'
            placeholder: Department
            type: text
            validate:
                required: false
        -
            name: field
            label: 'Field of Research'
            placeholder: 'Field of Research'
            type: text
            validate:
                required: true
        -
            name: description
            label: 'Please tell us a little more about your project and needs.'
            placeholder: 'Describe your project here.'
            type: textarea
            validate:
                required: true
    buttons:
        -
            type: submit
            value: Submit
    process:
        -
            email:
                from: '{{ config.plugins.email.from }}'
                to: ['{{ config.plugins.email.from }}', '{{ form.value.email }}']
                subject: '[Feedback] {{ form.value.name|e }}'
                body: '{% include ''forms/data.html.twig'' %}'
        -
            save:
                fileprefix: feedback-
                dateformat: Ymd-His-u
                extension: txt
                body: '{% include ''forms/data.txt.twig'' %}'
        -
            message: 'Thank you for contacting us. We will be in touch with you shortly.'
        -
            display: thankyou
---


---
title: 'Get Started'
description: 'This form helps us to better understand your needs and prepare us for your initial consultation. Please answer the following questions to the best of your ability, if you do not know the answer to a question it is fine to write "I do not know"'
form:
    name: contact-form
    fields:
        -
            name: name
            label: 'Name of Person Filling This Out'
            placeholder: Name
            autofocus: 'on'
            autocomplete: 'on'
            type: text
            validate:
                required: true
        -
            name: email
            label: 'Email of Person Filling This Out'
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
            my_field: null
            type: checkboxes
            label: 'Are you filling this form out on behalf of another researcher?'
            default:
                option1: false
                option2: false
            options:
                option1: 'Yes'
                option2: 'No'
            validate:
                required: true
        -
            name: behalfname
            label: 'Researcher Name (if filling this form out on behalf of another researcher)'
            placeholder: Name
            autofocus: 'on'
            autocomplete: 'on'
            type: text
            validate:
                required: true
        -
            name: behalfemail
            label: 'Researcher Email (if filling this form out on behalf of another researcher)'
            placeholder: Email
            type: email
            validate:
                required: true
        -
            name: behalfdepartment
            label: 'Researcher Department and/or Institution (if filling this form out on behalf of another researcher)'
            placeholder: Department
            type: text
            validate:
                required: false
        -
            name: behalfresearch
            label: 'Researcher Field of Research (if filling this form out on behalf of another researcher)'
            placeholder: 'Field of Research'
            type: text
            validate:
                required: true
        -
            name: currentresearch
            label: '1. What are your current research projects?'
            placeholder: 'Describe your project here.'
            type: textarea
            validate:
                required: true
        -
            name: projecttimeline
            label: '1a. What are the timelines of the projects?'
            placeholder: 'Please describe here.'
            type: textarea
            validate:
                required: true
        -
            name: hardwareresourcesforcomputation
            label: '2. What hardware resources are you currently using for computation?'
            placeholder: 'Please describe here.'
            type: textarea
            validate:
                required: true
        -
            name: meetcompneeds
            label: '2a. Do these meet your computational needs?'
            placeholder: 'Please describe here.'
            type: textarea
            validate:
                required: true
        -
            name: limitationsofresources
            label: '2b. Are there things you cannot do with your current resource that you would like to? (e.g., can you evaluate all the data you want to at the scale you want?)'
            placeholder: 'Please describe here.'
            type: textarea
            validate:
                required: true
        -
            name: otherresources
            label: '2c. Are you interested in using other resources? (e.g., our local cluster or national resources.)'
            placeholder: 'Please describe here.'
            type: textarea
            validate:
                required: true
        -
            name: softwareresearch
            label: '3. What software programs, packages, etc. are you using for your research?'
            placeholder: 'Please describe here.'
            type: textarea
            validate:
                required: true
        -
            name: existingissues
            label: '3a. Are there existing issues/limitations with the current software?'
            placeholder: 'Please describe here.'
            type: textarea
            validate:
                required: true
        -
            name: softwareyouwouldlike
            label: '3b. Is there software you would like to use? Is there a reason you are not currently using it?'
            placeholder: 'Please describe here.'
            type: textarea
            validate:
                required: true
        -
            name: softwaredevelopment
            label: '4. What software development/software engineering resources and/or personnel are you using?'
            placeholder: 'Please describe here.'
            type: textarea
            validate:
                required: true
        -
            name: softwaredevelopmentneeds
            label: '4a. Do these meet your software development needs?'
            placeholder: 'Please describe here.'
            type: textarea
            validate:
                required: true
        -
            name: sustainablesoftware
            label: '4b. Are you interested in using sustainable software practices? (e.g., code versioning, code reviews, testing.)'
            placeholder: 'Please describe here.'
            type: textarea
            validate:
                required: true
        -
            name: resourceforstorage
            label: '5. What resource are you using for storage?'
            placeholder: 'Please describe here.'
            type: textarea
            validate:
                required: true
        -
            name: howmuchstorageusing
            label: '5a. How much storage are you using?'
            placeholder: 'Please describe here.'
            type: textarea
            validate:
                required: true
        -
            name: howmuchstorageneeded
            label: '5b. How much storage will you need?'
            placeholder: 'Please describe here.'
            type: textarea
            validate:
                required: true
        -
            name: correctclassstorage
            label: '5c. Is this the correct class of storage for your work?'
            placeholder: 'Please describe here.'
            type: textarea
            validate:
                required: true
        -
            name: roadblocksresources
            label: '6. Are there any roadblocks to the use of computation resources in your current research?'
            placeholder: 'Please describe here.'
            type: textarea
            validate:
                required: true
        -
            name: networkissues
            label: '6a. Network issues?'
            placeholder: 'Please describe here.'
            type: textarea
            validate:
                required: true
        -
            name: knowledgeexpertise
            label: '6b. Knowledge/expertise?'
            placeholder: 'Please describe here.'
            type: textarea
            validate:
                required: true
        -
            name: hardware
            label: '6c. Hardware?'
            placeholder: 'Please describe here.'
            type: textarea
            validate:
                required: true
        -
            name: futureresearch
            label: '7. Where do you see your research going in the future?'
            placeholder: 'Please describe here.'
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


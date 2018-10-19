# Generating client code

It's possible to generate client code using the API Blueprint apiary.apib file.

For a walkthrough see https://apimatic.docs.apiary.io/#introduction/working-with-api-descriptions-documents

Sample:

Validate the API description by sending http post request to https://apimatic.io/api/validate

header: Authorization: your_key_from_https://apimatic.io

body: content from apiary.apib

Then for code generation send http post request to https://apimatic.io/api/codegen?name=gost&format=API%20;Blueprint&template=cs_portable_net_lib

header: Authorization: your_key_from_https://apimatic.io

body: content from apiary.apib

Result of this request is a link to a zip file with the generated code, something like https://apimatic.io/api/code-generations/5bc59db85f73f/generated-sdk.

Supported languages (template parameter): cs_portable_net_lib , java_eclipse_jre_lib , java_gradle_android_lib , objc_cocoa_touch_ios_lib , angular_javascript_lib , ruby_generic_lib , python_generic_lib ￼ , php_generic_lib ￼ , node_javascript_lib ￼ , go_generic_lib

Java is free while other languages are free only for the first two weeks after creating an Apimatic account...

# ubml

Small utility to generate html from the `index.ubml` xml file.

Always start .ubml files with a parent `<ubml>` tag.

Each direct child of this element will create a seperate output in the build folder. This is meant to create translated versions of ubml docs.

````html
<ubml>
    <en>
        <!-- -->
    </en>
</ubml>
````

will produce `./build/index_en.html`.

The blocks directory contains all the template "components" that ubml will understand. If a template is not found, the xml tag will be directly used as html. However, if the tagName is found to be a recognized block, the html template will replace the xml tag. Arguments can be passed to the html components using the ubml tag's arguments.

````html
<header text="My Website!" color="#ff0000" />
````

Within the blocks, these arguments can be used to customize the components.

````html
<!-- _header.html -->
<div style="width: 100%; height: 500px;background-color:@@color{#000000}@">
    @@text{Example Text}@
</div>
````

The replacement syntax takes the form

`@@attributeName{defaultValue}@`

The `./blocks/_index.html` file will be the base parent element of the output html file.
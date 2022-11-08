
# CKEditor 5 vue 3 component

This package is a custom vue 3 component for CKEditor 5, which is developed to connect [CKEditor 5 image manager plugin](https://github.com/amir94rp/ckeditor5-image-manager-plugin) and [laravel vue 3 image manager](https://github.com/amir94rp/laravel-file-manager).
## Installation

Install with npm

```bash
npm i @amir94rp/ckeditor5-vue3-component
```

## Usage/Examples

```vue
<template>
    <ckeditor :editor="editor"
              v-model="editorData"
              :config="editorConfig"
              @open="open = true"
              ref="editor">
    </ckeditor>

    <ImageManager v-model:open="open"
                  @output="insert"
                  :alt="alt"
                  :quality="quality"
                  :multiple="multiple"
                  :select="select"/>
</template>

<script>
import CKEditor from '@amir94rp/ckeditor5-vue3-component';
import ClassicEditor from '@amir94rp/ckeditor5-custom-build';
import ImageManager from "@amir94rp/vue3-file-manager";

export default {
    data(){
        return{
            open:false,
            multiple:true,
            select:true,
            quality:'xl',
            alt:false,

            editor: ClassicEditor,
            editorData: '',
            editorConfig: {
                fontFamily:{

                }
            },
        }
    },

    components:{
        ImageManager,
        ckeditor: CKEditor.component,
    },

    methods:{
        insert:function (value){
            this.$refs.editor.$_insertImages(value);
        },
    },
}
</script>
```


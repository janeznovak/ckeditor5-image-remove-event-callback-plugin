<template>
  <div id="app">
    <p>{{ editedObject }}</p>
    <div class="ck-container">
      <ckeditor
        class="ck-content"
        :editor="editor"
        v-model="editorData"
        :config="editorConfig"
      ></ckeditor>
    </div>
    <div class="ck-container">

      <p class="ck-content" v-html="editorData">{{ editorData }}</p>
    </div>
  </div>
</template>

<script>
import ClassicEditor from "@ckeditor/ckeditor5-editor-classic/src/classiceditor";

import EssentialsPlugin from "@ckeditor/ckeditor5-essentials/src/essentials";
import BoldPlugin from "@ckeditor/ckeditor5-basic-styles/src/bold";
import ItalicPlugin from "@ckeditor/ckeditor5-basic-styles/src/italic";
import LinkPlugin from "@ckeditor/ckeditor5-link/src/link";
import ParagraphPlugin from "@ckeditor/ckeditor5-paragraph/src/paragraph";
import SourceEditing from "@ckeditor/ckeditor5-source-editing/src/sourceediting";
import GeneralHtmlSupport from "@ckeditor/ckeditor5-html-support/src/generalhtmlsupport";
import ImageRemoveEventCallbackPlugin from "../plugins/ckeditor5-image-remove-event-callback-plugin/src/ImageRemoveEventCallbackPlugin";

export default {
  name: "editorDisplay",
  data() {
    return {
      editedObject: "",
      showEditor: false,
      editor: ClassicEditor,
      editorData: "<p>Content of the editor.</p>",
      editorConfig: {
        plugins: [
          EssentialsPlugin,
          BoldPlugin,
          ItalicPlugin,
          SourceEditing,
          LinkPlugin,
          ParagraphPlugin,
          GeneralHtmlSupport,
          ImageRemoveEventCallbackPlugin,
        ],
        extraPlugins: [],
        toolbar: {
          items: [
            "bold",
            "italic",
            "link",
            "sourceEditing",
          ],
        },
        htmlSupport: {
          allow: [
            {
              name: /.*/,
              attributes: true,
              classes: true,
              styles: true,
            },
          ],
        },
      },
    };
  },
  methods: {
    async imageRemove(images) {
		/** HANDLE THE IMAGE DELETION IN YOUR PARENT COMPONENT */
      console.log("in imageRemove");
			console.log("This is image: ", images);
		},
  },
  created() {
    console.log("In created");
    this.editorConfig.imageRemoveEvent = { callback: this.imageRemove };
  },
};
</script>

<style>
.sendLandingPage {
  /* margin-top: 10px; */
  margin: 0 auto;
  /* text-align: center; */
}

/* .ck-container {
} */

.ck-editor-btn {
  display: block;
  margin: 10px auto;
  float: none !important;
}

/* .center {
  
} */
</style>

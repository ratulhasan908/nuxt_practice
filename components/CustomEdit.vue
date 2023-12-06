<template>
    <div class="hello">
        <quill-editor v-model="content" ref="myQuillEditor" :options="editorOption" @blur="onEditorBlur($event)"
            @focus="onEditorFocus($event)" @ready="onEditorReady($event)"></quill-editor>
    </div>
</template>
  
<script>
import "quill/dist/quill.core.css";
import "quill/dist/quill.snow.css";
import { quillEditor, Quill } from "vue-quill-editor";
import { ImageExtend, QuillWatch } from "quill-image-extend-module";

Quill.register("modules/ImageExtend", ImageExtend);

export default {
    name: "HelloWorld",
    components: {
        quillEditor
    },
    props: {
        msg: String
    },
    data() {
        return {
            content: "",
            editorOption: {
                modules: {
                    ImageExtend: {
                        loading: true,
                        // name: "img",
                        // action: "https://jsonplaceholder.typicode.com/posts/",

                        headers: xhr => {
                            xhr.setRequestHeader("withCredentials", true);
                        },
                        response: res => {
                            return res.info;
                        }
                    },
                    toolbar: {
                        container: [
                            [
                                { size: ["small", false, "large", "huge"] },
                                { header: [1, 2, 3, 4, 5, 6, false] }
                            ],
                            [
                                "bold",
                                "italic",
                                "underline",
                                "strike",
                                { color: [] },
                                { background: [] }
                            ],
                            [
                                { list: "ordered" },
                                { list: "bullet" },
                                { indent: "-1" },
                                { indent: "+1" }
                            ],
                            ["link", "image"],
                            ["clean"]
                        ],
                        handlers: {
                        }
                    }
                }
            },
            onEditorBlur() { },
            onEditorFocus() { },
            onEditorReady(editor) { }
        };
    },
    watch: {
        content(val) {
            console.log(val);
        }
    },
    computed: {
        editor() {
            return this.$refs.myQuillEditor;
        }
    }
};
</script>
  
<style scoped>
h3 {
    margin: 40px 0 0;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    display: inline-block;
    margin: 0 10px;
}

a {
    color: #42b983;
}
</style>
  
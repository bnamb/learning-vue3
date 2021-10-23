<template>
    <div class="flex flex-wrap w-full text-gray-700 mb-10">
        <h1 class="w-full m-auto text-center text-3xl my-4">Markdown App</h1>
        <p class="text-center w-full mb-2">Add HTML elements to plaintext</p>
        <section class="flex m-auto h-screen w-10/12">
        <article class="w-1/2 border">
        <textarea class="w-full h-full p-2" :v-model="text" @input="update" placeholder="Type here..."></textarea>
        </article>
        <div id="markdown" class="w-1/2 border bg-gray-100 p-2 font-sans" v-html="markedText"></div>
        </section>
    </div>
</template>

<script>
import marked from 'marked';
import debounce from '../utilities/mixins/debounce';

export default {
    mixins: [debounce],
    data() {
        return {
            text:"",
        }
    },
    computed: {
        markedText(){
            return marked(this.text)
        }
    },
    methods: {
        update(e) {
             const task = () => (this.text= e.target.value);
             this.debounce(task, 500)
        },
    }
}
</script>

<style>
#markdown h1 {
display: block;
font-size: 2em;
margin-top: 0.67em;
margin-bottom: 0.67em;
margin-left: 0;
margin-right: 0;
font-weight: bold;
}
#markdown h2 {
display: block;
font-size: 1.5em;
margin-top: 0.83em;
margin-bottom: 0.83em;
margin-left: 0;
margin-right: 0;
font-weight: bold;
}
#markdown h3 {
display: block;
font-size: 1.17em;
margin-top: 1em;
margin-bottom: 1em;
margin-left: 0;
margin-right: 0;
font-weight: bold;
}
#markdown h4 {
display: block;
font-size: 1em;
margin-top: 1.33em;
margin-bottom: 1.33em;
margin-left: 0;
margin-right: 0;
font-weight: bold;
}
#markdown h5 {
display: block;
font-size: .83em;
margin-top: 1.67em;
margin-bottom: 1.67em;
margin-left: 0;
margin-right: 0;
font-weight: bold;
}
#markdown h6 {
display: block;
font-size: .67em;
margin-top: 2.33em;
margin-bottom: 2.33em;
margin-left: 0;
margin-right: 0;
font-weight: bold;
}
#markdown ul {
  display: block;
  list-style-type: disc;
  margin-top: 1em;
  margin-bottom: 1 em;
  margin-left: 0;
  margin-right: 0;
  padding-left: 40px;
}
#markdown ol {
  display: block;
  list-style-type: decimal;
  margin-top: 1em;
  margin-bottom: 1em;
  margin-left: 0;
  margin-right: 0;
  padding-left: 40px;
}
#markdown li {
  display: list-item;
}
</style>
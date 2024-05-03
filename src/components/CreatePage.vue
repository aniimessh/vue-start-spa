<template>
    <div class="container mb-3">
        <form action="">
        <div>
         <div class="mb-3">
         <label for="" class="form-label">
         Page Title
         </label>
         <input type="text" class="form-control" v-model="pageTitle"/>
         </div>
         <div class="mb-3">
         <label for="" class="form-label">
         Content
         </label>
         <textarea type="text" rows="5" class="form-control" v-model="pageContent"/>
         </div>
        </div>
        <div class="cols">
            <div class="mb-3">
            <label for="" class="form-label">
            Link text
            </label>
            <input type="text" v-model="pageLink" class="form-control" />
            </div>
            <div class="mb-3">
            <label for="" class="form-label">
            Page URL
            </label>
            <input type="text" v-model="pageURL" class="form-control" />
            </div>
            <div class=" row mb-3">
            <div class="form-check">
                <input type="checkbox" class="form-check-input" v-model="published" />
                <label for="" class="form-label">Published</label>
            </div>
            </div>
        </div>
         <div class="mb-3">
            <button type="" class="btn btn-primary" @click.prevent="submitForm" :disabled="isFormValid">
            Create Page
            </button>
         </div>
        </form>
    </div>
</template>

<script >
export default{
    props:["pageCreated"],
    computed: {
        isFormValid(){
            return !this.pageTitle || !this.pageContent || !this.pageLink || !this.pageURL
        }
    },
    data(){
        return {
            pageTitle: "",
            pageContent: "",
            pageLink: "",
            pageURL: "",
            published: true
        }
    },
    methods:{
        submitForm(){
            if(!this.pageTitle || !this.pageContent || !this.pageLink || !this.pageURL || !this.published){
                alert("Please Fill the form");
                return;
            }

            this.pageCreated({
                pageTitle: this.pageTitle,
                pageContent: this.pageContent,
                link:{
                    text: this.pageLink,
                    url: this.pageURL
                },
                published: this.published
            })

            pageTitle: '';
            pageContent: '';
            pageLink: '';
            pageURL: '';
            published: true
        }
    },
    watch: {
        pageTitle(newTitle, oldTitle){
            if(this.pageLink == oldTitle){
                this.pageLink = newTitle
            }
        }
    },
}
</script>


<style>
    
</style>
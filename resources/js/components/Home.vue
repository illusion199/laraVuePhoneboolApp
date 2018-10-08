<template>
    <div>
        <div class="list-group">
            <a href="#" class="list-group-item list-group-item-action active">
                VueJs Phonebook App
                <button class="btn btn-outline-info pull-right" @click="openAddModal">
                    Add New
                </button>
                <span class="is-pulled-right" v-if="loading">
                    <i class="fa fa-refresh fa-spin fa-2x fa-fw"></i>
                </span>
            </a>


            <a href="#" class="list-group-item list-group-item-action">
                <div class="inner-addon left-addon">
                    <i class="fa fa-search glyphicon" aria-hidden="true"></i>
                    <input type="text" class="form-control" placeholder="Search" />
                </div>
            </a>
            <!-- <ul>
    <li v-for="(item, key) in lists">{{item}}</li>
</ul> -->
            <a class="list-group-item list-group-item-action is-active" v-for="(item, key) in lists">
                <div class="row">
                    <div class="col col-md-9 col-sm-6">

                        <i class="text-primary fa fa-id-badge"><span class="text-danger"> {{item.name}}</span></i>
                    </div>
                    <div class="col col-md-1 col-sm-2">
                        <i class="text-warning fa fa-trash" aria-hidden="true" @click="del(key,item.id)"></i>
                    </div>
                    <div class="col col-md-1 col-sm-2">
                        <i class="text-success fa fa-edit" aria-hidden="true" @click="openUpdate(key)"></i>
                    </div>
                    <div class="col col-md-1 col-sm-2">
                        <i class="text-info fa fa-eye" aria-hidden="true" @click="openShow(key)"></i>
                    </div>

                </div>

            </a>


        </div>

        <Add-Modal :openModal="AddActiveClass" :mshow="mshow" @closeRequest="close"></Add-Modal>
        <Show :openModal="ShowActiveClass" :mshow="mshow" @closeRequest="close"></Show>
        <Update :openModal="UpdateActiveClass" :mshow="mshow" @closeRequest="close"></Update>
    </div>
</template>
<script>
    let AddModal = require("./AddModal.vue");
    let Show = require("./Show.vue");
    let Update = require("./Update.vue");
    export default {
        components: {
            AddModal,
            Show,
            Update
        },
        data() {
            return {
                AddActiveClass: "",
                ShowActiveClass: "",
                UpdateActiveClass: "",
                mshow: "",
                loading: false,
                lists: {},
                errors: {}
            };
        },
        mounted() {
            axios
                .post("/getData")
                .then(response => (this.lists = response.data))
                .catch(error => (this.errors = error.response.data.errors));
        },
        methods: {
            openAddModal() {
                this.AddActiveClass = "is-active";
                this.mshow = "show";
                //this.$emit('bitton-clicked');
            },
            openShow(key) {
                //console.log(key);
                //console.log(this.$children[1]);
                this.$children[1].list = this.lists[key];
                this.ShowActiveClass = "is-active";
                this.mshow = "show";
                //this.$emit('bitton-clicked');
            },
            openUpdate(key) {
                console.log(key);
                //console.log(this.$children[2]);
                this.$children[2].list = this.lists[key];
                this.UpdateActiveClass = "is-active";
                this.mshow = "show";
                //this.$emit('bitton-clicked');
            },
            del(key, id) {
                if (confirm("Are you sure ?")) {
                    this.loading = !this.loading;
                    axios
                        .delete(`/phonebook/${id}`)
                        .then(response => {
                            this.lists.splice(key, 1);
                            this.loading = !this.loading;
                        })
                        .catch(error => (this.errors = error.response.data.errors));
                }
                console.log(`${key} ${id}`);
            },
            close() {
                this.AddActiveClass = this.ShowActiveClass = this.UpdateActiveClass = "";
                this.mshow = "";
            }
        }
    };

</script>

<template>
    <div>
        <div class="list-group">
            <a href="#" class="list-group-item list-group-item-action active">
                VueJs Phonebook App
                <button class="btn btn-outline-info pull-right" @click="openAddModal">
                    Add New
                </button>
            </a>


            <a href="#" class="list-group-item list-group-item-action">
                <div class="inner-addon left-addon">
                    <i class="fa fa-search glyphicon" aria-hidden="true"></i>
                    <input type="text" class="form-control" placeholder="Search" />
                </div>
            </a>

            <a class="list-group-item list-group-item-action is-active">
                <div class="row">
                    <div class="col-md-9 col-sm-6">

                        <i class="text-primary fa fa-id-badge"><span class="text-danger"> Bulma</span></i>
                    </div>
                    <div class="col-md-1 col-sm-2">
                        <i class="text-warning fa fa-trash" aria-hidden="true" @click="del(key,item.id)"></i>
                    </div>
                    <div class="col-md-1 col-sm-2">
                        <i class="text-success fa fa-edit" aria-hidden="true" @click="openUpdate(key)"></i>
                    </div>
                    <div class="col-md-1 col-sm-2">
                        <i class="text-info fa fa-eye" aria-hidden="true" @click="openShow(key)"></i>
                    </div>

                </div>

            </a>

            <!--  <a href="#" class="list-group-item list-group-item-action disabled">Vestibulum at eros</a> -->


            <!-- <a class="list-group-item list-group-item-action is-active">
    <div class="row">
        <span class="col-sm-9">

            <i class="text-primary fa fa-id-badge"><span class="text-danger"> Bulma</span></i>
        </span>
        <span class="col-sm-1">
            <i class="text-warning fa fa-trash" aria-hidden="true" @click="del(key,item.id)"></i>
        </span>
        <span class="col-sm-1">
            <i class="text-success fa fa-edit" aria-hidden="true" @click="openUpdate(key)"></i>
        </span><span class="col-sm-1">
            <i class="text-info fa fa-eye" aria-hidden="true" @click="openShow(key)"></i>
        </span>

    </div>

</a> -->

        </div>
        <!--  <nav class="panel column is-offset-2 is-8">
            <p class="panel-heading">
                VueJs Phonebook App
                <button class="button is-primary is-outlined" @click="openAddModal">
                    Add New
                </button>
            </p>
            <div class="panel-block">
                <p class="control has-icons-left">
                    <input class="input is-small" type="text" placeholder="search">
                    <span class="icon is-small is-left">
                        <i class="fa fa-search" aria-hidden="true"></i>
                    </span>
                </p>
            </div>

            <a class="panel-block is-active">
                <span class="panel-icon column is-9">
                    <i class="fa fa-book" aria-hidden="true">Bulma</i>
                </span>


                <span class="panel-icon column is-1">
                    <i class="has-text-danger fa fa-trash" aria-hidden="true" @click="del(key,item.id)"></i>
                </span>
                <span class="panel-icon column is-1">
                    <i class="has-text-info fa fa-edit" aria-hidden="true" @click="openUpdate(key)"></i>
                </span><span class="panel-icon column is-1">
                    <i class="has-text-primary fa fa-eye" aria-hidden="true" @click="openShow(key)"></i>
                </span>
            </a>

        </nav> -->
        <Add-Modal :openModal="AddActiveClass" :mshow="mshow" @closeRequest="close"></Add-Modal>
    </div>
</template>
<script>
    let AddModal = require("./AddModal.vue");
    export default {
        components: {
            AddModal
        },
        data() {
            return {
                AddActiveClass: '',
                mshow: '',
                lists: {},
                errors: {}
            };
        },
        mounted() {
            axios.post("/getData")
                .then((response) => this.lists = response.data)
                .catch((error) => this.errors = error.response.data.errors)
        },
        methods: {
            openAddModal() {
                this.AddActiveClass = "is-active";
                this.mshow = "show";
                //this.$emit('bitton-clicked');

            },
            close() {
                this.AddActiveClass = "";
                this.mshow = "";
            }
        }
    };

</script>

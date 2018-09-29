<template>
    <div>
        <nav class="panel column is-offset-2 is-8">
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

        </nav>
        <Add-Modal :openModal="AddActiveClass"></Add-Modal>
    </div>
</template>
<script>
    let AddModal = require('./AddModal.vue')
    export default {
        components: {
            AddModal
        },
        data() {
            return {
                AddActiveClass: ''
            }
        },
        methods: {
            openAddModal() {
                this.AddActiveClass = 'is-active'
            }

        }
    }

</script>

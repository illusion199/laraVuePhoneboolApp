<template>
    <div class="modalWapper">
        <!-- Button trigger modal -->
        <!--   <button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModalCenter">
            Launch demo modal
        </button> -->

        <!-- Modal -->

        <div class="modal fade" :class="[openModal, mshow]">
            <div class="modal-dialog modal-dialog-centered" role="document">
                <div class="modal-content">
                    <div class="modal-header">
                        <h5 class="modal-title" id="exampleModalCenterTitle">Modal title</h5>
                        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                            <span aria-hidden="true" @click="close">&times;</span>
                        </button>
                    </div>
                    <div class="modal-body">

                        <div class="form-group">
                            <label for="name">Name</label>
                            <input type="text" :class="{'border-warning':errors.name}" name="name" class="form-control"
                                aria-describedby="emailHelp" placeholder="Name" v-model="list.name">
                            <small id="emailHelp" class="form-text text-muted">We'll never share your email with
                                anyone else.</small>
                            <small class="text-warning" v-if="errors.name">{{errors.name[0]}}</small>
                        </div>
                        <div class="form-group">
                            <label for="phone">Phone Number</label>
                            <input type="text" :class="{'border-warning':errors.phone}" name="phone" class="form-control"
                                placeholder="Phone Number" v-model="list.phone">
                            <small class="text-warning" v-if="errors.phone">{{errors.phone[0]}}</small>
                        </div>
                        <div class="form-group">
                            <label for="email">Email address</label>
                            <input type="email" :class="{'border-warning':errors.email}" name="email" class="form-control"
                                aria-describedby="emailHelp" placeholder="Enter email" v-model="list.email">
                            <small id="emailHelp" class="form-text text-muted">We'll never share your email with
                                anyone else.</small>
                            <small class="text-warning" v-if="errors.email">{{errors.email[0]}}</small>
                        </div>

                        <!--   <button type="submit" class="btn btn-primary">Submit</button> -->

                    </div>
                    <div class="modal-footer">
                        <button type="button" class="btn btn-secondary" data-dismiss="modal" @click="close">Close</button>
                        <button type="button" class="btn btn-primary" @click="save">Save</button>
                    </div>
                </div>
            </div>
        </div>


    </div>
</template>
<script>
    export default {
        props: ["openModal", "mshow"],
        data() {
            return {
                list: {
                    name: "",
                    phone: "",
                    email: ""
                },
                errors: {}
            };
        },
        methods: {
            close() {
                this.$emit("closeRequest");
            },
            save() {
                axios
                    .post("/phonebook", this.$data.list)
                    .then((response) => {
                        this.close()
                        this.$parent.lists.push(response.data)
                        this.$parent.lists.sort(function (a, b) {
                            if (a.name > b.name) {
                                return 1;
                            } else if (a.name < b.name) {
                                return -1;
                            }
                        })
                        this.list = ""
                    })
                    .catch((error) => this.errors = error.response.data.errors)
            }
        }
    };

</script>

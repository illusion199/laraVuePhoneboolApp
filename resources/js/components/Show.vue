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
                        <h5 class="modal-title" id="exampleModalCenterTitle">{{list.name}}'s <i>Details</i></h5>
                        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                            <span aria-hidden="true" @click="close">&times;</span>
                        </button>
                    </div>
                    <div class="modal-body">

                        <div class="form-group">
                            <label for="name"><strong>Name:</strong></label>

                            <span>{{list.name}}</span>

                        </div>
                        <div class="form-group">
                            <label for="phone"><strong>Phone Number:</strong></label>
                            <span>{{list.phone}}</span>
                        </div>
                        <div class="form-group">
                            <label for="email"><strong>Email address:</strong></label>

                            <span>{{list.email}}</span>

                        </div>

                        <!--   <button type="submit" class="btn btn-primary">Submit</button> -->

                    </div>
                    <div class="modal-footer">
                        <button type="button" class="btn btn-secondary" data-dismiss="modal" @click="close">Close</button>

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
                list: ''
            }
        },
        methods: {
            close() {
                this.$emit("closeRequest");
            },
        }
    };

</script>

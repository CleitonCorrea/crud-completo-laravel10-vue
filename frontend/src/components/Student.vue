<template>
    <div class="container">
        <div class="row">
            <div class="col-md-4">
                <div class="card-header">
                    Add Registro
                </div>
                <div class="card-body">
                    <form @submit.prevent="save" >

                        <div class="form-group">
                        <label>Name</label>
                        <input type="text" class="form-control" placeholder="name">
                        </div>

                        <div class="form-group">
                        <label>Address</label>
                        <input type="text" class="form-control" placeholder="address">
                        </div>

                        <div class="form-group">
                        <label>Phone</label>
                        <input type="text" class="form-control" placeholder="phone">
                        </div>

                    <button type="submit" class="btn btn-primary">Salvar</button>
                    </form>
                </div>
            </div><!--fim row-->

            <div class="col-md-8">
                <h2>Student List</h2>
                <table class="table table-dark">
                    <thead>
                        <tr>
                            <th scope="col">ID</th>
                            <th scope="col">Name</th>
                            <th scope="col">Address</th>
                            <th scope="col">Phone</th>
                            <th scope="col">Actions</th>
                        </tr>
                    </thead>

                    <tbody>
                        <tr v-for="student in result" v-bind:key="student.id">
                            <td>{{student.id}}</td>
                            <td>{{student.name}}</td>
                            <td>{{student.address}}</td>
                            <td>{{student.phone}}</td>
                            <td>
                                <button type="button" class="btn btn-primary">Edit</button>
                                <button type="button" class="btn btn-danger">Delete</button>
                            </td>
                        </tr>
                    </tbody>

                </table>

            </div>

        </div>
    </div>
</template>
<script>
import axios from 'axios';

export default{

    name: 'Student',
    data(){
        return{
            result: {},
            student: {
                id: '',
                name: '',
                address: '',
                phone: ''
            }
        }
    },

    created(){
        this.StudentLoad();
    },

    mounted(){
        console.log('mouted() called...');
    },

    methods:{
        StudentLoad(){

            axios
      .get('http://127.0.0.1:8000/api/students/')
      .then(({data}) =>{
        console.log(data);
        this.result = data;
    } )

        },
    }


}
</script>

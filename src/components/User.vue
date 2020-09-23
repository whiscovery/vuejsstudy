<template>
  <div class="blue lighten-3 pa-3">
    <h1>User 컴포넌트</h1>
    <p>이름: {{name}} <v-btn color="info"  @click="changeName()">변경</v-btn></p>
    <p>{{ getDateAndTime(createdAt) }}</p>
    <hr>
    <v-layout row wrap>
      <v-flex xs12 sm6>
        <UserDetail 
            :name="name"
            :address="address"
            :phone="phone"
            :hasDog="hasDog"
        >
        </UserDetail>
      </v-flex>
      <v-flex xs12 sm6>
        <UserEdit
            :name="name"
            :address="address"
            :phone="phone"
            :hasDog="hasDog"
            @child="parents"
        ></UserEdit>
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
import UserDetail from './UserDetail.vue'
import UserEdit from './UserEdit.vue'
import { dateFormat } from '../mixins/dateFormat'
    
export default {
    components: {
        UserDetail, UserEdit
    },
    data () {
        return {
            name: '진욱',
            address: '광주',
            phone: '0100100101',
            hasDog: false,
            createdAt: null

        }
    },
    created() {
        this.createdAt = new Date()
    },
    methods: {
        changeName () {
            this.name = '정진욱'

        },
        parents(user){
            this.name = user.name,
            this.address = user.address,
            this.phone = user.phone,
            this.hasDog = user.hasDog
        }
    },
    mixins: [dateFormat]
}
</script>
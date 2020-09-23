<template>
  <div class="red lighten-3 pa-3">
    <h3>자세한 회원 정보를 확인합니다.</h3>
    <p>상세사항</p>
    <p>이름 : {{name}}</p>
    <p>주소 : {{address}}</p>
    <p>전화 : {{phone}}</p>
    <p>개유무: {{hasDogConfirm}}</p>
    <p>수정일: {{getDateAndTime(editedDate)}}</p>
  </div>
</template>

<script>
import { eventBus } from "../main"
import { dateFormat } from "../mixins/dateFormat"

export default {
    props: [ 'name', 'address', 'phone', 'hasDog'],
    data () {
        return {
            editedDate: ''
        }
    },
    computed: {
        hasDogConfirm() {
            return this.hasDog ? 'Yes':'No'
        }
    },
    created() {
        eventBus.$on('userWasEdited', (date) => {
            this.editedDate = date
        })
    },
    mixins: [dateFormat]
}
</script>

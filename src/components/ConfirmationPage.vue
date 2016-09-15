<template>
    <div class="form-group">
        <p>
            <strong>
                TTL to be deducted: <var style="color:red">AUD {{ttlValue}}</var>
            </strong>
            <br>
            <small><var style="color:red">({{sendValue}} + AUD {{transferFee}})</var></small>
        <p>
        <p>
            <strong>
                Amount to be received:
                <var style="color:green">{{receiveValue}}</var>
            </strong>
            <br>
            <small><var style="color:blue">({{sendValue}} * {{exRate}})</var></small>
        </p>
        <hr/>
        <form>
            <label class="radio-inline">
                <input type="radio" value="bank" v-model="method">Bank
            </label>
            <label class="radio-inline">
                <input type="radio" value="cash" v-model="method"> Cash
            </label>
            <small class="pull-right clickable">
                Contacts
                <span class="glyphicon glyphicon-user"></span>
            </small>
        </form>
        <br>
        <div class="input-group">
            <input class="form-control" placeholder='Name: i.e. Jane Doe' />

            <span v-show="method=='bank'">
                <input class="form-control" placeholder='BSB No. i.e. xxx-xxx' />
                <input class="form-control" placeholder='Account No. i.e. xxxx' />
            </span>

            <span v-show="method=='cash'">
                <input class="form-control" placeholder='Home address i.e. 20 Bulv. ..' />
                <input class="form-control" placeholder='Phone No. i.e. +01402xxx' />
            </span>
        </div>
        <br>
        <button class="btn btn-primary" @click="currentView='mainPage'">
             <span class="glyphicon glyphicon-arrow-left"></span> Go back
        </button>

        <button class="btn btn-danger pull-right" @click="currentView='summaryPage'">
            Confirm <span class="glyphicon glyphicon-send"></span>
        </button>
    </div>
</template>

<script>

export default {
    props: [
        'sendValue',
        'exRate',
        'receiveValue',
        'transferFee',
        'ttlValue',
        'currentView',
    ],

    data () {
        return {
            method: 'bank'
        }
    },

}
</script>

<style scoped>

.form-control {
    margin-top: 5px;
}

</style>

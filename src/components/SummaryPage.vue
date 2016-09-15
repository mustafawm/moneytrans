<template>
    <div class="form-group">
        <p>
            <strong>
                Amount deducted:
                <var style="color:red">AUD {{ttlValue}}</var>
            </strong>
            <br>
            <small>
                Exchange Rage: {{exRate}} <br/>
                Transfer Fees: {{transferFee}}
            </small>
        </p>
        <hr/>
        <p>
            <strong>
                Amount to receive:
                <var style="color:green">AUD {{receiveValue}}</var>
            </strong>
            <br>
            <small>
                Transfer may take 2 - 4 buisness days
            </small>
        </p>
        <br>
        <center>
            <button class="btn btn-success center" @click="currentView='mainPage'">
            Done <span class="glyphicon glyphicon-home"></span>
            </button>
        </center>
    </div>
</template>

<script>

export default {
    props: ['receiveValue', 'exRate', 'transferFee', 'ttlValue', 'currentView'],

    data () {
        return {
        }
    },

}
</script>

<style>



</style>

<template>
    <div>
        <div class="form-group">
            <label>Select destination currency:</label>

            <select class="form-control" v-model="selected">

                <option v-for="cur in currencies" :value="cur.text">
                    {{ cur.text }} &nbsp;&nbsp; {{cur.value}}
                </option>
            </select>
            {{selected.text}}
        </div>

        <div class="form-group">
            <label for="sendValue">Initial amount to send:</label>
            <div class="input-group">
                <div class="input-group-addon">AUD</div>
                <input v-model="sendValue"
                    type="number" class="form-control"
                    placeholder=110.00 name="sendValue"
                >
            </div>
        </div>
        <div class="form-group">
            <label for="receiveValue">Will receive
                <small class="text-primary">(initial amount * {{exRate}}):</small>
            </label>
            <div class="input-group">
                <div class="input-group-addon">{{selected}}</div>
                <input v-model="receiveValue"
                    type="number" class="form-control"
                    placeholder=102.45 name="receiveValue"
                >
            </div>
        </div>
        <div class="form-group">
            <label for="ttl">TTL to be deducted
                <small class="text-primary">(initial amount + {{transferFee}}):</small>
            </label>
            <div class="input-group">
                <div class="input-group-addon">AUD</div>
                <input
                    v-model="ttlValue" readonly
                    type="number" class="form-control"
                    placeholder=110.00 name="ttl"
                >
            </div>
        </div>

        <div class="form-gorup">
            <button
                @click="currentView='ConfirmationPage'"
                class="btn btn-success pull-right"
            >
                Proceed
                <span class="glyphicon glyphicon-arrow-right"></span>
            </button>
        </div>
    </div>
</template>

<script>

export default {
    props: {
        currencies  : [],
        sendValue   : 0,
        receiveValue: 0,
        ttlValue    : 0,
        transferFee : 30,
        exRate      : 0,
        selected    : '',
        currentView : '',
    },

    data () {
        return {
        }
    }
}
</script>

<style >

</style>

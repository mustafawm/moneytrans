<template>
    <div id="app">
        <div class="panel panel-default">
            <div class="panel-heading">
                <h3 class="panel-title">
                    <span
                        @click="currentView='mainPage'"
                        class="clickable glyphicon glyphicon-home">
                    </span>
                    MoneyTrans
                    <span
                        @click="currentView='infoPage'"
                        class="clickable glyphicon glyphicon-info-sign pull-right">
                    </span>
                </h3>
            </div>
            <div class="panel-body">
                <component :is="currentView"
                    :current-view.sync = "currentView"
                    :currencies="currencies"
                    :send-value.sync = "sendValue"
                    :receive-value.sync = "receiveValue"
                    :ttl-value.sync = "ttlValue"
                    :transfer-fee.sync = "transferFee"
                    :ex-rate.sync = "exRate"
                    :selected.sync = "currency"
                >

                </component>

            </div>
        </div>
    </div>
</template>

<script>
import MainPage from './components/MainPage.vue'
import InfoPage from './components/InfoPage.vue'
import ConfirmationPage from './components/ConfirmationPage.vue'
import SummaryPage from './components/SummaryPage.vue'

export default {
    components: {
        MainPage,
        InfoPage,
        ConfirmationPage,
        SummaryPage
    },
    ready() {
        // fetch ex rate from API
        var that = this;
        this.$http.get('http://api.fixer.io/latest?base=AUD').then((response) => {
            for (var i in response.body.rates) {
                that.currencies.push({text: i, value: response.body.rates[i]});
            }
        }, (response) => {
            console.error('API ERROR: ' + response);
        });
    },
    // App data
    data () {
        return {
            currentView: 'mainPage',
            currencies: [],
            exRate: .75,
            transferFee: 33,
            sendValue: 0,
            receiveValue: 0,
            ttlValue:0,
            currency: 'USD'
        }
    },
    // Watching changes and acting accordingly
    watch: {
        sendValue(val, oldVal) {
            this.receiveValue = (+val  * +this.exRate).toFixed(2);
            this.ttlValue = (+val + +this.transferFee).toFixed(2)
        },
        receiveValue(val, oldVal) {
            this.sendValue = (+val/+this.exRate).toFixed(2);
            this.ttlValue = (+this.sendValue + +this.transferFee).toFixed(2)
        },
        currency(val, oldVal) {
            this.currencies.forEach( (i) => {
                if (i.text === val) {
                    this.exRate = i.value;
                }
            });
        }
    }
}
</script>

<style>
body {
    font-family: Helvetica, sans-serif;
}
</style>

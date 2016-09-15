<template>
    <div class="form-group">
        <p>
            <strong>Converting to {{selected}}:</strong>
            <var style="color:red">AUD {{sendValue}}</var> <strong>&times;</strong>
                <abbr title="current market exchange rate"><var>{{exRate}}</var></abbr> &equals;
                <var style="color:green">{{selected}} {{converted}} </var>
        </p>
        <p>
            <strong>Transfer fee:</strong>
            <var style="color:red">AUD {{transferFee}}</var></p>
        <hr/>
        <p>
            <strong>TTL to be deducted:</strong>
            <var style="color:red">{{sendValue}}</var> +
            <var style="color:red">AUD {{transferFee}}</var> &equals;
            <var style="color:red">AUD {{ttlValue}}</var>
        </p>
    </div>
</template>

<script>

export default {
    props: ['sendValue', 'exRate', 'converted', 'transferFee', 'ttlValue', 'selected'],

    data () {
        return {
        }
    },

}
</script>

<style>



</style>

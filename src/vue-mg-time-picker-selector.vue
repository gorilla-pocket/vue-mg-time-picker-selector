<template>
    <div class="d-flex">
        <div class="mr-1">
            <select class="form-control" v-model="selected_minute" :class="{ 'is-invalid': isInvalid }">
                <option></option>
                <option v-for="minute in minutes" :key="minute.value" :value="minute.value">{{minute.value}}</option>
            </select>
        </div>
        <div class="align-self-center mr-1">
            分
        </div>
        <div class="mr-1">
            <select class="form-control" v-model="selected_second" :class="{ 'is-invalid': isInvalid }">
                <option></option>
                <option v-for="second in seconds" :key="second.value" :value="second.value">{{second.value}}</option>
            </select>
        </div>
        <div class="align-self-center">
            秒
        </div>
    </div>
</template>

<script>
export default {
    props: {
        value: {
            default: '',
        },
        isInvalid: {
            default: false,
        },
        minMinute: {
            default: 1,
        },
        maxMinute: {
            default: 20,
        },
        secondRange: {
            default: 10,
        }
    },
    data () {
        return {
            selected_minute: '',
            selected_second: '',
        }
    },
    mounted: function () {
        // console.log(this.value)
        if (this.value) {
            let d = this.value.split(':')
            const hour = parseInt(d[0])
            this.selected_minute = hour * 60 + parseInt(d[1])
            this.selected_second = parseInt(d[2])
        }
    },
    watch: {
        value: function (val) {
            if (!val) {
                this.selected_minute = ''
                this.selected_second = ''
                return
            }
            let d = val.split(':')
            const hour = parseInt(d[0])
            this.selected_minute = hour * 60 + parseInt(d[1])
            this.selected_second = parseInt(d[2])
        },
        selected_minute: function () {
            let ret = this.convertDate()
            this.$emit('input', ret)
        },
        selected_second: function () {
            let ret = this.convertDate()
            this.$emit('input', ret)
        },
    },
    computed: {
        minutes: function () {
            const minutes = []
            for (let i = this.minMinute; i <= this.maxMinute; i++) {
                minutes.push({
                    value: i
                });
            }
            return minutes
        },
        seconds: function () {
            const seconds = []
            for (let i = 0; i <= 50; i = i + this.secondRange) {
                seconds.push({
                    value: i
                });
            }
            return seconds
        },
    },
    methods: {
        convertDate: function () {
            let ret = ''
            if (String(this.selected_minute) != '' && String(this.selected_second) != '') {
                const hour = parseInt(this.selected_minute / 60)
                const minute = parseInt(this.selected_minute) % 60
                ret = ('00' + hour).slice(-2)+':'+('00' + minute).slice(-2)+':'+('00' + this.selected_second).slice(-2)
            }
            return ret
        }
    },
    components: {
        //
    }
}
</script>
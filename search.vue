<template>
    <div :class="prefixCls">
        <!--<i-input-->
            <!--v-model="currentQuery"-->
            <!--size="small"-->
            <!--:icon="icon"-->
            <!--:placeholder="placeholder"-->
            <!--@on-click="handleClick"></i-input>-->
      <Select   clearable
                @on-change="seachSelectChange"
                @on-clear = "seachClear"
      >
        <Option v-for="item in selectData" :value="item.label" :key="item.id">{{ item.label }}</Option>
      </Select>
    </div>
</template>
<script>

    export default {
        name: 'Search',
        props: {
            prefixCls: String,
            placeholder: String,
            query: String,
            selectData:Array
        },
        data () {
            return {
                currentQuery: this.query
            };
        },
        watch: {
            query (val) {
                this.currentQuery = val;
            },
            currentQuery (val) {
                this.$emit('on-query-change', val);
            }
        },
        computed: {
            icon () {
                return this.query === '' ? 'ios-search' : 'ios-close-circle';
            }
        },
        methods: {
            handleClick () {
                if (this.currentQuery === '') return;
                this.currentQuery = '';
                this.$emit('on-query-clear');
            },
          seachSelectChange(item){
            this.$emit('on-select-change',item);
          },
          seachClear(){
            this.$emit('on-search-clear','')
          }
        }
    };
</script>

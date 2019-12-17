# Transfer
>vue Transfer 修改使用下拉框搜索</p>

```
      <ATransfer
              v-if="memberModalVisible1"
              class="workStationTransfer"
              :data="equipments"
              :target-keys="selectedEqu"
              :selectData="selectData"
              :titles="['可选人员列表','已选人员列表']"
              :render-format="renderFormate"
              :filter-method = "fliterMethod"
              filterable
              @on-change="handleChange2"
            />
```

>selectData是个数组
>fliterMethod是过滤的方法可以自定义
```
//data 是列表中的每一个item query是下拉框选中的值 query可以根据自己的需求去修改
//返回boolean值 返回true 显示 返回false 不显示
filterMethod(data, query){
  
}
```

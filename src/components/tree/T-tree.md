# tree
> ### 文件说明:
    tree ———+———— T-tree.vue: vue单文件组件，UI组件源码，包含template,js,css
            |———— T-tree.js : tree组件出口文件
> ### 组件说明
    1.组件调用
        
      步骤一：引入tree 组件文件夹
      步骤二：在父组件js中引入组件  import {Tree} from './components/tree/T-tree.js'
      步骤三：在父组件中注册 Tree 组件
      步骤四：在相应的节点处添加Tree节点并绑定数据  <Tree :data="data"></Tree> 
    
    2.组件使用
    <Tree 
      :data="data" 
      @checkEvent="getEvent" 
      checkBox 
    />
      
    data:  
      data ———— tree组件渲染的数据集合，数据类型为 数组(Array),必传    
      data=[{
        id: 'nodeId1 nodeId2',
        class: 'nodeClass1 nodeclass2',
        style: 'font-size: 16px; background: red;',
        uid: '野马汽车',
        label: '一级',
        children: [{
          label: '二级',
          children: [{label: '三级'}]
        }]
      }]
      label ———— 节点标题，必传
      children ———— 子节点数据，可选
      id ———— 在相应节点增加 id，可选
      class ———— 在相应节点增加 class，可选
      style ———— 在相应节点增加 style，可选
      uid ———— 唯一标识，可选

    checkBox: 带勾选框的 tree
    checkEvent: 选中之后获取到勾选节点的数据集合，回调函数有一个接收数据的参数


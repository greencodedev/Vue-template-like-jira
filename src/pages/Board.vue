<template>
    
  <div class="container">

    <el-row :gutter="30">
      <el-col :span="6">

        <h3 class="box-card-title">Outcomes</h3>
        <el-card class="box-card header">
          <el-button type="info" icon="el-icon-plus" circle
            @click="showAddingPopup = true; addPopupTitle = 'Outcomes'"></el-button>
        </el-card>
        <!-- /.box-card (header) -->

        <div class="overflow-wrapper">
          <div class="drop-wrapper" 
            v-bind:class="{'active': isDragging && selectedArr !== outcomes}">
            <div
              v-for="(item, index) in outcomes" 
              :key="item.id"
              v-on:mousedown="selectItem(index, item, outcomes)"
              v-on:mouseup="dropItem(index, outcomes)"
              v-bind:class="{'dragging': isItemDragging(item)}"
              :id="item.id"
              class="box-card-item-wrapper">

              <el-card class="box-card item">

                <h4 class="name">
                  <el-badge is-dot>{{item.name}}</el-badge>
                </h4>
                <div class="avatar"><el-avatar shape="circle" :size="'small'" :src="''"></el-avatar></div>
                <div class="tags">
                  <el-button type="primary" size="mini" round>Text</el-button>
                  <el-button type="success" size="mini" round>Text</el-button>
                  <el-button type="warning" size="mini" round>Text</el-button>
                  <i class="el-icon-s-tools"></i>
                </div>

              </el-card>
            </div>
            <!-- /.box-card (item) -->
            <div
              v-if="isDragging && outcomes.length < 1"
              v-on:mouseup="dropItem(0, outcomes)"
              class="box-card-item-wrapper empty">

              <el-card class="box-card item"></el-card>
            </div>
            <!-- /.box-card (empty) -->
          </div>
          <!-- /.drop-wrapper -->
        </div>
        <!-- /.overflow-wrapper -->

      </el-col>
      <el-col :span="6">

        <h3 class="box-card-title">Products</h3>
        <el-card class="box-card header">
          <el-button type="info" icon="el-icon-plus" circle
            @click="showAddingPopup = true; addPopupTitle = 'Products'"></el-button>
        </el-card>
        <!-- /.box-card (header) -->

        <div class="overflow-wrapper">
          <div class="drop-wrapper" 
            v-bind:class="{'active': isDragging && selectedArr !== products}">
            <div
              v-for="(item, index) in products" 
              :key="item.id"
              v-on:mousedown="selectItem(index, item, products)"
              v-on:mouseup="dropItem(index, products)"
              v-bind:class="{'dragging': isItemDragging(item)}"
              :id="item.id"
              class="box-card-item-wrapper">

              <el-card class="box-card item">

                <h4 class="name">
                  <el-badge is-dot>{{item.name}}</el-badge>
                </h4>
                <div class="avatar"><el-avatar shape="circle" :size="'small'" :src="''"></el-avatar></div>
                <div class="tags">
                  <el-button type="primary" size="mini" round>Text</el-button>
                  <el-button type="success" size="mini" round>Text</el-button>
                  <el-button type="warning" size="mini" round>Text</el-button>
                  <i class="el-icon-s-tools"></i>
                </div>

              </el-card>
            </div>
            <!-- /.box-card (item) -->
            <div
              v-if="isDragging && products.length < 1"
              v-on:mouseup="dropItem(0, products)"
              class="box-card-item-wrapper empty">

              <el-card class="box-card item"></el-card>
            </div>
            <!-- /.box-card (empty) -->
          </div>
          <!-- /.drop-wrapper -->
        </div>
        <!-- /.overflow-wrapper -->

      </el-col>
      <el-col :span="6">

        <h3 class="box-card-title">Projects</h3>
        <el-card class="box-card header">
          <el-button type="info" icon="el-icon-plus" circle
            @click="showAddingPopup = true; addPopupTitle = 'Projects'"></el-button>
        </el-card>
        <!-- /.box-card (header) -->

        <div class="overflow-wrapper">
          <div class="drop-wrapper" 
            v-bind:class="{'active': isDragging && selectedArr !== projects}">
            <div
              v-for="(item, index) in projects" 
              :key="item.id"
              v-on:mousedown="selectItem(index, item, projects)"
              v-on:mouseup="dropItem(index, projects)"
              v-bind:class="{'dragging': isItemDragging(item)}"
              :id="item.id"
              class="box-card-item-wrapper">

              <el-card class="box-card item">

                <h4 class="name">
                  <el-badge is-dot>{{item.name}}</el-badge>
                </h4>
                <div class="avatar"><el-avatar shape="circle" :size="'small'" :src="''"></el-avatar></div>
                <div class="tags">
                  <el-button type="primary" size="mini" round>Text</el-button>
                  <el-button type="success" size="mini" round>Text</el-button>
                  <el-button type="warning" size="mini" round>Text</el-button>
                  <i class="el-icon-s-tools"></i>
                </div>

              </el-card>
            </div>
            <!-- /.box-card (item) -->
            <div
              v-if="isDragging && projects.length < 1"
              v-on:mouseup="dropItem(0, projects)"
              class="box-card-item-wrapper empty">

              <el-card class="box-card item"></el-card>
            </div>
            <!-- /.box-card (empty) -->
          </div>
          <!-- /.drop-wrapper -->
        </div>
        <!-- /.overflow-wrapper -->

      </el-col>
      <el-col :span="6">

        <h3 class="box-card-title">Tools</h3>
        <el-card class="box-card header">
          <el-button type="info" icon="el-icon-plus" circle
            @click="showAddingPopup = true; addPopupTitle = 'Tools'"></el-button>
        </el-card>
        <!-- /.box-card (header) -->
        
        <div class="overflow-wrapper">
          <div class="drop-wrapper"
            v-bind:class="{'active': isDragging && selectedArr !== tools, 'empty': tools.length < 1}">
            <div
              v-for="(item, index) in tools" 
              :key="item.id"
              v-on:mousedown="selectItem(index, item, tools)"
              v-on:mouseup="dropItem(index, tools)"
              v-bind:class="{'dragging': isItemDragging(item)}"
              :id="item.id"
              class="box-card-item-wrapper">

              <el-card class="box-card item">

                <h4 class="name">
                  <el-badge is-dot>{{item.name}}</el-badge>
                </h4>
                <div class="avatar"><el-avatar shape="circle" :size="'small'" :src="''"></el-avatar></div>
                <div class="tags">
                  <el-button type="primary" size="mini" round>Text</el-button>
                  <el-button type="success" size="mini" round>Text</el-button>
                  <el-button type="warning" size="mini" round>Text</el-button>
                  <i class="el-icon-s-tools"></i>
                </div>

              </el-card>
            </div>
            <!-- /.box-card (item) -->
            <div
              v-if="isDragging && tools.length < 1"
              v-on:mouseup="dropItem(0, tools)"
              class="box-card-item-wrapper empty">

              <el-card class="box-card item"></el-card>
            </div>
            <!-- /.box-card (empty) -->
          </div>
          <!-- /.drop-wrapper -->
        </div>
        <!-- /.overflow-wrapper -->

      </el-col>
    </el-row>

    <el-dialog
      :title="'Add new item to ' + addPopupTitle"
      :visible.sync="showAddingPopup"
      width="40%">
      <div>
        <el-input placeholder="Name" v-model="inputItemName"></el-input>
      </div>
      <span slot="footer" class="dialog-footer">
        <el-button @click="showAddingPopup = false">Cancel</el-button>
        <el-button type="primary" @click="addItem(addPopupTitle)">Confirm</el-button>
      </span>
    </el-dialog>

  </div>

</template>

<script>
export default {
  name: 'BoardPage',
  methods: {

    selectItem(index, item, arr) {
      this.selectedIndex = index;
      this.selectedItem = item;
      this.selectedArr = arr;

      const selectedHtmlElOrig = document.querySelector('#' + item.id);
      this.selectedHtmlEl = selectedHtmlElOrig.cloneNode(true);
      this.selectedHtmlEl.style.width = selectedHtmlElOrig.clientWidth + 'px';
      this.selectedHtmlEl.style.position = 'fixed';

      document.body.appendChild(this.selectedHtmlEl);

      this.isMouseDown = true; 

    },

    dragItem(event) {

      if(!this.isDragging)
        return;

      if(this.selectedHtmlEl) {

        const x = event.x - this.selectedHtmlEl.clientWidth / 2;
        const y = event.y - this.selectedHtmlEl.clientHeight - 5;

        this.selectedHtmlEl.style.top = y + 'px';
        this.selectedHtmlEl.style.left = x + 'px';

      }

    },

    dropItem(index, arr) {

      if(!this.isDragging)
        return;

      this.deleteItem(this.selectedIndex, this.selectedArr);

      arr.splice(index, 0, this.selectedItem);

      this.isMouseDown = false;

    },

    deleteItem(index, arr) {

      arr.splice(index, 1);

    },

    isItemDragging(item) {

      if(this.isDragging && this.selectedItem && item.id === this.selectedItem.id)
        return true;

      return false;

    },

    addItem(type) {

      if(!this.inputItemName)
        return;


      this.showAddingPopup = false;

      const item = {
        name: this.inputItemName,
        id: ''
      }

      switch(type) {

        case 'Outcomes':
          item.id = type + this.outcomes.length;
          this.outcomes.push(item);
          break;
        case 'Products':
          item.id = type + this.products.length;
          this.products.push(item);
          break;
        case 'Projects':
          item.id = type + this.projects.length;
          this.projects.push(item);
          break;
        case 'Tools':
          item.id = type + this.tools.length;
          this.tools.push(item);
          break;

      }

      this.inputItemName = '';

    }

  },
  created() {

    window.addEventListener('mousemove', (event) => {

      if(this.isMouseDown)
        this.isDragging = true;
      else
        this.isDragging = false;

      this.dragItem(event);

    });

    window.addEventListener('mouseup', () => {

      if(this.selectedHtmlEl && this.selectedHtmlEl.parentNode)
        this.selectedHtmlEl.parentNode.removeChild(this.selectedHtmlEl);

      this.isMouseDown = false;

    });

  },
  data() {
    return {

      debug: true,

      isMouseDown: false,
      isDragging: false,

      selectedIndex: null,
      selectedItem: null,
      selectedHtmlEl: null,
      selectedArr: null,

      outcomes: [
        { name: 'Enhance Brand', id: 'outcome1' },
        { name: 'Grow Revenue', id: 'outcome2' },
        { name: 'Grow Stakeholder', id: 'outcome3' },
        { name: 'Increase Social Footprint', id: 'outcome4' }
      ],

      products: [
        { name: 'Compensation', id: 'product1' },
        { name: 'Other Added Project', id: 'product2' },
        { name: 'Policy Development', id: 'product3' },
        { name: 'Talent Management', id: 'product4' },
        { name: 'Product 5', id: 'product5' }
      ],

      projects: [
        { name: 'Project 1', id: 'project1' },
        { name: 'Project 2', id: 'project2' },
        { name: 'Project 3', id: 'project3' },
        { name: 'Project 4', id: 'project4' },
        { name: 'Project 5', id: 'project5' }
      ],

      tools: [
        { name: 'Tool 1', id: 'tool1' },
        { name: 'Tool 2', id: 'tool2' },
        { name: 'Tool 3', id: 'tool3' },
        { name: 'Tool 4', id: 'tool4' },
        { name: 'Tool 5', id: 'tool5' }
      ],

      showAddingPopup: false,
      addPopupTitle: '',
      inputItemName: ''

    }
  }
}
</script>

<style lang="scss" scoped>

  .box-card-title {
    font-size: 14px;
    font-weight: bold;
    text-transform: uppercase;
  }

  .overflow-wrapper {
    overflow-y: auto;
    max-height: calc(100vh - 170px);
    padding: 15px 15px 15px;
    margin: 10px -15px 0px;
  }

  .drop-wrapper {
    border-radius: 4px;
    cursor: move;

    &.active {
      border: 2px dashed #409eff;

      &:hover {
        border-color: #67C23A;
      }
    }

  }

  .box-card {

    &.header {
      margin-top: 5px;
      text-align: center;
      max-height: 56px;

      button {
        font-size: 25px;
        padding: 7px;
        margin-top: -13px;
      }

    }

    &.item {
      -webkit-touch-callout: none;
      -webkit-user-select: none;
      -khtml-user-select: none;
      -moz-user-select: none;
      -ms-user-select: none;
      user-select: none;

      .name .el-badge {
        display: block;
      }

      .avatar, .tags {
        margin-top: 10px;
      }

      .tags {

        button {
          padding: 3px 7px;
          font-size: 11px;
        }

        i {
          float: right;
          font-size: 21px;
          margin-top: -1px;
          margin-right: -10px;
          color: #C0C4CC;
        }

      } 

    }

  }

  .box-card-item-wrapper {
    cursor: move;

    &:not(:first-child) {
      padding-top: 10px;
    }

    &.dragging {
      opacity: 0.5;
    }

    &.empty {

      .el-card {
        min-height: 125px;
        background-color: rgba(#409eff, .2)
      }

      &:hover {

        .el-card {
          background-color: rgba(#67C23A, .2)
        }

      }

    }

  }

</style>
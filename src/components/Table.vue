<template>
  <div class="ra-table">
    <el-table
      class="ra-table-main"
      :data="tableData"
    >
      <el-table-column
        prop="name"
        label="Name"
        width="180"
      ></el-table-column>
      <el-table-column
        prop="age"
        label="Age"
      ></el-table-column>
      <el-table-column
        prop="gender"
        label="Gender"
      ></el-table-column>
      <el-table-column
        prop="price"
        label="Price"
      ></el-table-column>
      <el-table-column
        label="Operations"
      >
        <template slot-scope="scope">
          <el-button
            size="mini"
            @click="handleMore(scope.$index, scope.row)"
          >
            More
          </el-button>
          <el-button
            size="mini"
            type="success"
            @click="handleBuy(scope.$index, scope.row)"
          >
            Buy
          </el-button>
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
  import names from '@/data/names'

  export default {
    data: () => ({
      tableData: []
    }),
    
    mounted() {
      this.faker()
    },

    methods: {
      faker() {
        for (let index = 0; index < 50; index++) {
          this.tableData.push({
            name: this.generateName(),
            age: this.generateAge(),
            gender: this.generateGender(),
            price: this.generatePrice()
          })
        }
      },

      generateName() {
        return names[Math.floor(Math.random() * (49 - 1) + 1)]
      },

      generateAge() {
        return Math.floor(Math.random() * (90 - 3)) + 3
      },

      generateGender() {
        if(Math.random() < 0.5) return 'male'
        else return 'female'
      },
      
      generatePrice() {
        return Math.floor(Math.random() * (50000 - 500) + 300)
      }
    }
  }
</script>

<style lang="scss" scoped>
  .ra-table {
    display: grid;
    grid-template-columns: 800px;
    align-items: center;
    justify-content: center;
    padding-top: 50px;
    &-main {
      width: 100%;
    }
  }
</style>

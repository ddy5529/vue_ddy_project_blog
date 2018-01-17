<template>
  <div>
    <el-tabs type="border-card">
      <el-tab-pane label="计算器">
        <el-tabs :tab-position="tabPosition" style="">
          <el-tab-pane label="普通计算器">普通计算器</el-tab-pane>
          <el-tab-pane label="特殊计算器">
            <el-collapse v-model="activeName" accordion>
              <el-collapse-item title="计算通胀后的购买力" name="1">
                <div>
                  <el-form>
                    <el-form-item>
                      本金（元）:
                      <el-input
                        placeholder="请输入本金"
                        v-model="tableData[0].oldmoney"
                        clearable>
                      </el-input>
                    </el-form-item>
                    <el-form-item>
                      每年的通胀率（%）:
                      <el-input
                        placeholder="请输入平均每年的通胀率"
                        v-model="tableData[0].inflation_rate"
                        clearable>
                      </el-input>
                    </el-form-item>
                    <el-form-item>
                      年限（y）：
                      <el-input
                        placeholder="请输入多少年"
                        v-model="tableData[0].inputyear"
                        clearable>
                      </el-input>
                    </el-form-item>
                    <el-form-item>
                      多年后您输入的<span> {{tableData[0].oldmoney}}</span> 将变成 <span
                      style="color: red">{{tableData[0].toltalmoney}}</span>
                    </el-form-item>
                    <el-form-item>
                      <el-button type="primary" @click="gettotalmoney">立即创建</el-button>
                    </el-form-item>
                  </el-form>
                  <p>财富贬值计算：</p>
                  <el-table
                    border
                    :data="tableData"
                    style="width: 100%"
                    height="250">
                    <el-table-column
                      fixed
                      prop="inputyear"
                      label="年限"
                      width="150">
                    </el-table-column>
                    <el-table-column
                      prop="inflation_rate"
                      label="通胀率"
                      width="120">
                    </el-table-column>
                    <el-table-column
                      prop="oldmoney"
                      label="本金"
                      width="120">
                    </el-table-column>
                    <el-table-column
                      prop="toltalmoney"
                      label="结果"
                      width="120">
                    </el-table-column>
                  </el-table>
                </div>
              </el-collapse-item>
              <el-collapse-item title="计算房价通账后价值" name="2">
                <div>
                  <el-form>
                    <el-form-item>
                      贷款金额：
                      <el-input
                        placeholder="请输入本金"
                        v-model="payforhouseoldmoney"
                        clearable>
                      </el-input>
                    </el-form-item>
                    <el-form-item>
                      贷款年限：
                      <el-select v-model="optionslabel" placeholder="请选择年份">
                        <el-option
                          v-for="item in options"
                          :key="item.value"
                          :label="item.label"
                          :value="item.value">
                        </el-option>
                      </el-select>
                    </el-form-item>
                    <el-form-item>
                      贷款方式：
                      <el-select v-model="payformoneylabel" placeholder="还款方式">
                        <el-option
                          v-for="item in payformoney"
                          :key="item.value"
                          :label="item.label"
                          :value="item.value">
                        </el-option>
                      </el-select>
                    </el-form-item>
                    <el-form-item>
                      贷款利率：
                      <el-select v-model="loaninterestlabel" placeholder="贷款利率">
                        <el-option
                          v-for="item in loaninterest"
                          :key="item.value"
                          :label="item.label"
                          :value="item.value">
                        </el-option>
                      </el-select>
                    </el-form-item>
                    <el-form-item>
                      <el-button @click="getshophoruseallloadmoney">计算</el-button>
                      <p>您总共要还的钱：<span style="color: red">{{toltalmoney}}</span></p>
                      <p>这些钱的购买力相当于本年的：<span style="color: red">{{yourloadmoneymoneyonthepurchasing}}</span></p>
                    </el-form-item>
                  </el-form>
                </div>
              </el-collapse-item>
            </el-collapse>

          </el-tab-pane>
        </el-tabs>
      </el-tab-pane>
      <el-tab-pane label="NULL">NULL——1</el-tab-pane>
      <el-tab-pane label="NULL">NULL——2</el-tab-pane>
      <el-tab-pane label="NULL">NULL——3</el-tab-pane>
    </el-tabs>
  </div>
</template>
<script>
  export default {
    components: {},
    data() {
      return {
        tabPosition: 'left',
        tabPositiontop: 'top',
        selectvalue: '',
        tableData: [{
          inputyear: 0,
          inflation_rate: 0,
          oldmoney: 0,
          toltalmoney: 0
        }],
        options: [{
          value: '0',
          label: '未选择'
        }, {
          value: '15',
          label: '十五年'
        }, {
          value: '20',
          label: '二十年'
        }, {
          value: '30',
          label: '三十年'
        }],
        payformoney: [
          {
            value: '1001',
            label: '等额本金'
          }, {
            value: '1002',
            label: '等额本息'
          }],
        loaninterest: [
          {
            value: '0.039',
            label: '3.9%'
          }, {
            value: '0.04',
            label: '4%'
          }, {
            value: '0.041',
            label: '4.1%'
          }],
        payforhouseoldmoney: '',
        optionslabel: '',
        payformoneylabel: '',
        loaninterestlabel: '',
        toltalloadmoney: '',
        yourloadmoneymoneyonthepurchasing: ''
      }
    },
    methods: {
      gettotalmoney: function() {
        this.tableData[0].toltalmoney = this.tableData[0].oldmoney * Math.pow((1 / (1 + this.tableData[0].inflation_rate * 0.01)), this.tableData[0].inputyear)
      },
      getshophoruseallloadmoney: function() {
        this.toltalmoney = '2'
        this.yourloadmoneymoneyonthepurchasing = '2'
      }
    }
  }
</script>

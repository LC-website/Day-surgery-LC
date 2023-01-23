<template>
  <div id="app">
    <el-row>
            <el-container>
                <el-header>
                    <h1 style="color:orange;">小儿肺炎住院费用 DRG 路径</h1>
                </el-header>
                <el-main>
                    <el-form ref="form" model="form" label-width="88px">
                        <el-form-item label="住院天数">
                            <el-select v-model="form.days" placeholder="请选择">
                                <el-option label="0-9 天" value="0-9 天"></el-option>
                                <el-option label="9-16 天" value="9-16 天"></el-option>
                                <el-option label="16-60 天" value="16-60 天"></el-option>
                                <el-option label="大于 60 天" value="大于 60 天"></el-option>
                            </el-select>
                        </el-form-item>
                        <el-form-item label="肺炎类型">
                            <el-select v-model="form.pneumonia_type" placeholder="请选择">
                                <el-option label="" value=""></el-option>
                                <el-option label="未特指生物体所致的肺炎" value="未特指生物体所致的肺炎"></el-option>
                                <el-option label="新生儿肺炎" value="新生儿肺炎"></el-option>
                                <el-option label="其他细菌性肺炎" value="其他细菌性肺炎"></el-option>
                                <el-option label="病毒性肺炎" value="病毒性肺炎"></el-option>
                                <el-option label="肺炎链球菌性肺炎" value="肺炎链球菌性肺炎"></el-option>
                                <el-option label="流感嗜血杆菌性肺炎" value="流感嗜血杆菌性肺炎"></el-option>
                                <el-option label="间质性肺炎" value="间质性肺炎"></el-option>
                                <el-option label="吸入性肺炎" value="吸入性肺炎"></el-option>
                                <el-option label="衣原体肺炎" value="衣原体肺炎"></el-option>
                            </el-select>
                        </el-form-item>
                        <el-form-item label="输血">
                            <el-select v-model="form.metachysis" placeholder="请选择">
                                <el-option label="" value=""></el-option>
                                <el-option label="无" value="无"></el-option>
                                <el-option label="有" value="有"></el-option>
                            </el-select>
                        </el-form-item>
                        <el-form-item label="手术">
                            <el-select v-model="form.operation" placeholder="请选择">
                                <el-option label="" value=""></el-option>
                                <el-option label="无" value="无"></el-option>
                                <el-option label="有" value="有"></el-option>
                            </el-select>
                        </el-form-item>
                        <el-form-item label="特级护理">
                            <el-select v-model="form.nursing" placeholder="请选择">
                                <el-option label="" value=""></el-option>
                                <el-option label="无" value="无"></el-option>
                                <el-option label="有" value="有"></el-option>
                            </el-select>
                        </el-form-item>
                        <el-form-item>
                            <el-button type="primary" @click="onSubmit">查询</el-button>
                        </el-form-item>
                    </el-form>
                    <div v-if="drg">
                        已进入 DRG 路径: {{drg}} ，费用为: {{DRG_price[drg]}} 元
                    </div>
                    <el-dialog title="提示" :visible.sync="dialogVisible" width="30%">
                        <span>不存在此 DRG 路径</span>
                        <span slot="footer" class="dialog-footer">
      <el-button type="primary" @click="dialogVisible = false">确 定</el-button>
      </span>
                    </el-dialog>
                </el-main>
            </el-container>
            <div class="grid-content bg-purple-light">&nbsp</div>
    </el-row>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

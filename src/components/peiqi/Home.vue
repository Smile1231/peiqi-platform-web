<template>
  <div class="gene_main">
    <el-menu
      :default-active="activeIndex"
      class="el-menu-demo"
      mode="horizontal"
      background-color="#eaeaea"
      text-color="#858585"
      @select="handleSelect"
    >
      <el-menu-item class="nav_first" @click="welcome"
        >Peiqi Deploy PlatFrom</el-menu-item
      >
      <!-- <el-menu-item index="1">about</el-menu-item>
      <el-menu-item index="2">
        <template slot="title">Cas-OFFinder</template> -->
      <!-- <el-menu-item index="2-1">选项1</el-menu-item>
        <el-menu-item index="2-2">选项2</el-menu-item>
        <el-menu-item index="2-3">选项3</el-menu-item>
        <el-submenu index="2-4">
          <template slot="title">选项4</template>
          <el-menu-item index="2-4-1">选项1</el-menu-item>
          <el-menu-item index="2-4-2">选项2</el-menu-item>
          <el-menu-item index="2-4-3">选项3</el-menu-item>
        </el-submenu> -->
      <!-- </el-menu-item>
      <el-menu-item index="3">Microhomology</el-menu-item>
      <el-menu-item index="4">Cas-Designer</el-menu-item>
      <el-menu-item index="5">DataBase</el-menu-item>
      <el-menu-item index="6">Analyzer</el-menu-item>
      <el-menu-item index="7">Digenome-Seq</el-menu-item>
      <el-menu-item index="8">Base Editing</el-menu-item> -->
    </el-menu>
    <div class="line"></div>
    <div class="gene_body">
      <div class="font_style">
        <h2>Pei Qi (EveryThing must be here)</h2>
        <h3>A PlatFrom to deploy application to CloudFoundry.</h3>
        <div class="p_all">
          <p>something i want to say</p>
        </div>
      </div>
      <div class="gene_panel">
        <el-container class="gene_container">
          <el-main class="gene_main">
            <!-- please Select a deployment mode-->
            <el-row :gutter="40">
              
              <!-- select mode -->
              <el-col :span="24"
                ><div class="grid-content bg-purple">
                  <div class="panel_all">
                    <div class="panel_title">
                      <h2>Please Select A Deployment Mode 🕊</h2>
                    </div>
                    <div class="panel_first_content">
                      <div class="content_subTitle">
                        <h4>
                          <!-- <a href="javascript:;" @click="downloadGZFile">
                            📝 &nbsp; download example
                          </a> -->
                        </h4>
                      </div>
                      <!-- checkbox -->
                      <div class="content_select">
                        <div>
                          <el-radio v-model="mtar_upload_mode" label="0" border
                            >Upload the MTAR package Involuntarily</el-radio
                          >
                          <el-radio v-model="mtar_upload_mode" label="1" border
                            >Upload the MTAR package Voluntarily</el-radio
                          >
                        </div>
                      </div>
                    </div>
                  </div>
                </div></el-col
              >
            </el-row>

            <!-- Please Select App you want to deply ⭐️ -->
            <el-row :gutter="40">
              <!-- <el-col :span="5">
                <div class="grid-content bg-purple-light"></div>
              </el-col> -->
              <!-- 第一行panel -->
              <el-col :span="24"
                ><div class="grid-content bg-purple">
                  <div class="panel_all" v-show="select_app_show">
                    <div class="panel_title">
                      <h2>Please Select App you want to deply ⭐️</h2>
                    </div>
                    <div class="panel_first_content">
                      <div class="content_subTitle">
                        <h4>
                          <!-- <a href="javascript:;" @click="downloadGZFile">
                            📝 &nbsp; download example
                          </a> -->
                        </h4>
                      </div>
                      <!-- checkbox -->
                      <div class="content_select">
                        <div>
                          <el-checkbox-group v-model="checkboxGroup1">
                            <el-checkbox-button
                              class="select_btn"
                              border
                              v-for="(item, index) in cities"
                              :label="item"
                              :key="item"
                              @change="select_app(index)"
                              >{{ item }}</el-checkbox-button
                            >
                          </el-checkbox-group>
                        </div>
                      </div>
                      <!-- select version  -->
                      <div class="content_file_upload">
                        <el-row :gutter="20">
                          <!-- select option -->
                          <el-col :span="4"
                            ><div class="grid-content bg-purple">
                              <div class="content_upload_gz">
                                <el-select
                                  clearable
                                  v-show="icaClientNode_show"
                                  v-model="ica_client_node_value"
                                  filterable
                                  placeholder="plz select"
                                >
                                  <el-option
                                    v-for="item in options"
                                    :key="item.value"
                                    :label="item.label"
                                    :value="item.value"
                                  >
                                  </el-option>
                                </el-select>
                              </div></div
                          ></el-col>
                          <el-col :span="4"
                            ><div class="grid-content bg-purple">
                              <el-select
                                clearable
                                v-show="server_show"
                                v-model="server_value"
                                filterable
                                placeholder="plz select"
                              >
                                <el-option
                                  v-for="item in options"
                                  :key="item.value"
                                  :label="item.label"
                                  :value="item.value"
                                >
                                </el-option>
                              </el-select></div
                          ></el-col>
                          <el-col :span="4"
                            ><div class="grid-content bg-purple">
                              <el-select
                                clearable
                                v-show="workSpace_show"
                                v-model="work_space_value"
                                filterable
                                placeholder="Plz select"
                              >
                                <el-option
                                  v-for="item in options"
                                  :key="item.value"
                                  :label="item.label"
                                  :value="item.value"
                                >
                                </el-option>
                              </el-select></div
                          ></el-col>
                        </el-row>
                        <el-alert
                          style="width: 70%"
                          title="select app name first , and select the version you want to deply !"
                          type="success"
                          :closable="false"
                        >
                        </el-alert>
                      </div>
                    </div>
                  </div></div
              ></el-col>
              <!-- <el-col :span="5"><div class="grid-content bg-purple"></div></el-col> -->
            </el-row>

            <!-- Plz upload mtar extension file -->
            <el-row :gutter="40">
              <el-col :span="24"
                ><div class="grid-content bg-purple">
                  <div class="panel_all" v-show="extension_mar_show">
                    <div class="panel_title">
                      <h2>Plz upload mtar extension file 🧩</h2>
                    </div>
                    <div class="panel_sec_content">
                      <div class="content_subTitle">
                        <h4>
                          <!-- Please upload a file with .xlsx suffix -->
                          <a
                            href="javascript:;"
                            @click="downloadMtarExtensionFile"
                          >
                            📝 &nbsp; download mtar extension file example
                          </a>
                        </h4>
                      </div>

                      <div class="content_input">
                        <div class="content_api_endpoint">
                          <div class="sub-title">API EndPoint</div>
                          <el-input
                            clearable
                            placeholder="Plz Input api address"
                            v-model="input_api_endpoint"
                          >
                            <template slot="prepend">https://</template>
                            <template slot="append">.com</template>
                          </el-input>
                        </div>
                        <div class="content_org_space">
                          <el-row class="demo-autocomplete">
                            <el-col :span="6">
                              <div class="sub-title">Org Name</div>
                              <el-autocomplete
                                clearable
                                class="inline-input"
                                v-model="org_name"
                                :fetch-suggestions="querySearch"
                                placeholder="Plz input org name"
                                @select="handleSelect"
                              ></el-autocomplete>
                            </el-col>
                            <el-col :span="8">
                              <div class="sub-title">Space Name</div>
                              <el-autocomplete
                                clearable
                                class="inline-input"
                                v-model="space_name"
                                :fetch-suggestions="querySearch"
                                placeholder="Plz input space name"
                                @select="handleSelect"
                              ></el-autocomplete>
                            </el-col>
                          </el-row>
                        </div>
                      </div>

                      <!-- file upload -->
                      <div class="content_mtar_file_upload">
                        <el-row :gutter="2" v-show="icaClientNode_show">
                          <el-upload
                            ref="XLSXUpload"
                            :action="uploadUrl"
                            :before-remove="beforeXLSXRemove"
                            :limit="1"
                            :accept="acceptXLSX"
                            :on-exceed="handleExceed"
                            :file-list="XLSXFileList"
                            :on-success="onXLSXSuccess"
                            :on-error="onError"
                            :auto-upload="false"
                          >
                            <!-- first button -->
                            <el-col :span="18"
                              ><div class="grid-content bg-purple">
                                <el-tooltip
                                  content="select icaCilentNode Mtar Extension File"
                                  placement="top"
                                >
                                  <div class="content_upload_xlsx">
                                    <el-button
                                      slot="trigger"
                                      size="medium"
                                      type="primary"
                                      >Click To Select File</el-button
                                    >
                                    <div slot="tip" class="el-upload__tip">
                                      Only Upload .matext File
                                    </div>
                                  </div>
                                </el-tooltip>
                              </div>
                            </el-col>
                            <el-col :span="4">
                              <div class="grid-content bg-purple">
                                <div class="content_upload_xlsx">
                                  <el-button
                                    size="medium"
                                    type="success"
                                    @click="submitXLSXUpload"
                                    >Upload File To Server</el-button
                                  >
                                </div>
                              </div>
                            </el-col>
                          </el-upload>
                        </el-row>

                        <!-- second button -->
                        <el-row :gutter="2" v-show="server_show">
                          <el-upload
                            class="upload-demo"
                            ref="XLSXUpload"
                            :action="uploadUrl"
                            :before-remove="beforeXLSXRemove"
                            :limit="1"
                            :accept="acceptXLSX"
                            :on-exceed="handleExceed"
                            :file-list="XLSXFileList"
                            :on-success="onXLSXSuccess"
                            :on-error="onError"
                            :auto-upload="false"
                          >
                            <el-col :span="18"
                              ><div class="grid-content bg-purple">
                                <el-tooltip
                                  content="select Server Mtar Extension File"
                                  placement="top"
                                >
                                  <div class="content_upload_xlsx">
                                    <el-button
                                      slot="trigger"
                                      size="medium"
                                      type="primary"
                                      >Click To Select File</el-button
                                    >
                                    <div slot="tip" class="el-upload__tip">
                                      Only Upload .matext File
                                    </div>
                                  </div>
                                </el-tooltip>
                              </div>
                            </el-col>
                            <el-col :span="4">
                              <div class="grid-content bg-purple">
                                <div class="content_upload_xlsx">
                                  <el-button
                                    size="medium"
                                    type="success"
                                    @click="submitXLSXUpload"
                                    >Upload File To Server</el-button
                                  >
                                </div>
                              </div>
                            </el-col>
                          </el-upload>
                        </el-row>

                        <!-- third button -->
                        <el-row :gutter="2" v-show="workSpace_show">
                          <el-upload
                            class="upload-demo"
                            ref="XLSXUpload"
                            :action="uploadUrl"
                            :before-remove="beforeXLSXRemove"
                            :limit="1"
                            :accept="acceptXLSX"
                            :on-exceed="handleExceed"
                            :file-list="XLSXFileList"
                            :on-success="onXLSXSuccess"
                            :on-error="onError"
                            :auto-upload="false"
                          >
                            <el-col :span="18"
                              ><div class="grid-content bg-purple">
                                <el-tooltip
                                  content="select WorkSpace Mtar Extension File"
                                  placement="top"
                                >
                                  <div class="content_upload_xlsx">
                                    <el-button
                                      slot="trigger"
                                      size="medium"
                                      type="primary"
                                      >Click To Select File</el-button
                                    >
                                    <div slot="tip" class="el-upload__tip">
                                      Only Upload .matext File
                                    </div>
                                  </div>
                                </el-tooltip>
                              </div>
                            </el-col>
                            <el-col :span="4">
                              <div class="grid-content bg-purple">
                                <div class="content_upload_xlsx">
                                  <el-button
                                    size="medium"
                                    type="success"
                                    @click="submitXLSXUpload"
                                    >Upload File To Server</el-button
                                  >
                                </div>
                              </div>
                            </el-col>
                          </el-upload>
                        </el-row>
                      </div>
                      <div class="editor-container">
                        <yaml-editor v-model="yaml_value" />
                      </div>

                      <!-- submit 按钮 -->
                      <div class="submit_button">
                        <el-button type="danger" size="big" @click="enterEmail"
                          >Deploy</el-button
                        >
                      </div>
                    </div>
                  </div>
                </div></el-col
              >
            </el-row>

            <!-- dialog  -->
            <el-dialog
              title="Upload Mtar And Extension To Deploy"
              :visible.sync="dialogVisible"
              width="50%"
              :before-close="handleCloseDialog"
            >
              <span>
                <el-form :model="form">
                  <el-form-item
                    label="API EndPoint"
                    :label-width="formLabelWidth"
                  >
                    <el-input
                      style="width: 50%"
                      clearable
                      placeholder="Plz Input api address"
                      v-model="input_api_endpoint"
                    >
                      <template slot="prepend">https://</template>
                      <template slot="append">.com</template>
                    </el-input>
                  </el-form-item>
                  <el-form-item label="Org Name" :label-width="formLabelWidth">
                    <el-autocomplete
                      clearable
                      class="inline-input"
                      v-model="org_name"
                      :fetch-suggestions="querySearch"
                      placeholder="Plz input org name"
                      @select="handleSelect"
                    ></el-autocomplete>
                  </el-form-item>
                  <el-form-item
                    label="Space Name"
                    :label-width="formLabelWidth"
                  >
                    <el-autocomplete
                      clearable
                      class="inline-input"
                      v-model="space_name"
                      :fetch-suggestions="querySearch"
                      placeholder="Plz input space name"
                      @select="handleSelect"
                    ></el-autocomplete>
                  </el-form-item>

                  <!-- upload mtar file -->
                  <el-form-item style="margin-bottom: 0px;">
                    <el-upload
                      class="upload-demo"
                      ref="XLSXUpload"
                      :action="uploadUrl"
                      :before-remove="beforeXLSXRemove"
                      :limit="1"
                      :accept="acceptXLSX"
                      :on-exceed="handleExceed"
                      :file-list="XLSXFileList"
                      :on-success="onXLSXSuccess"
                      :on-error="onError"
                      :auto-upload="false"
                    >
                      <el-col :span="18"
                        ><div class="">
                          <el-tooltip
                            content="select Mtar File"
                            placement="top"
                          >
                            <div class="content_upload_xlsx">
                              <el-button
                                slot="trigger"
                                size="medium"
                                type="primary"
                                >Click To Select Mtar File</el-button
                              >
                              <div slot="tip" class="el-upload_tip">
                                Only Upload .mtar File
                              </div>
                            </div>
                          </el-tooltip>
                        </div>
                      </el-col>
                      <el-col :span="4">
                        <div class="">
                          <div class="">
                            <el-button
                              size="medium"
                              type="success"
                              @click="submitXLSXUpload"
                              >Upload File To Server</el-button
                            >
                          </div>
                        </div>
                      </el-col>
                    </el-upload>
                  </el-form-item>

                  <!-- upload mtaext file -->
                  <el-form-item>
                    <el-upload
                      class="upload-demo"
                      ref="XLSXUpload"
                      :action="uploadUrl"
                      :before-remove="beforeXLSXRemove"
                      :limit="1"
                      :accept="acceptXLSX"
                      :on-exceed="handleExceed"
                      :file-list="XLSXFileList"
                      :on-success="onXLSXSuccess"
                      :on-error="onError"
                      :auto-upload="false"
                    >
                      <el-col :span="18"
                        ><div class="">
                          <el-tooltip
                            content="select MtaExt File"
                            placement="top"
                          >
                            <div class="content_upload_xlsx">
                              <el-button
                                slot="trigger"
                                size="medium"
                                type="primary"
                                >Click To Select MtaExt File</el-button
                              >
                              <div slot="tip" class="el-upload_tip">
                                Only Upload .mtar File
                              </div>
                            </div>
                          </el-tooltip>
                        </div>
                      </el-col>
                      <el-col :span="4">
                        <div class="">
                          <div class="">
                            <el-button
                              size="medium"
                              type="success"
                              @click="submitXLSXUpload"
                              >Upload File To Server</el-button
                            >
                          </div>
                        </div>
                      </el-col>
                    </el-upload>
                  </el-form-item>
                </el-form>
              </span>
              <span slot="footer" class="dialog-footer">
                <el-button type="info" @click="handleCloseDialog"
                  >cancel</el-button
                >
                <el-button type="danger" @click="dialogVisible = false"
                  >Deploy</el-button
                >
              </span>
            </el-dialog>
          </el-main>
        </el-container>
      </div>
    </div>

    <!-- 漂浮进度框 -->
    <div class="float_steps">
      <el-steps
        class="float_form"
        :active="active"
        direction="vertical"
        finish-status="success"
      >
        <el-step
          title="step 1"
          description="please select gz file and clink upload button"
        ></el-step>
        <el-step
          title="step 2"
          description="please select xlsx file and clink upload button"
        ></el-step>
        <el-step
          title="step 3"
          description="please click submit button,enter email and click confirm button"
        ></el-step>
      </el-steps>
    </div>
  </div>
</template>

<script>
import YamlEditor from "@/components/YamlEditor/index.vue";

const cityOptions = ["IAClietNode", "Server", "WorkSpace"];

const yamlData =
  '- hosts: all\n  become: yes\n  become_method: sudo\n  gather_facts: no\n\n  tasks:\n  - name: "install {{ package_name }}"\n    package:\n      name: "{{ package_name }}"\n      state: "{{ state | default(\'present\') }}"';

export default {
  data() {
    return {
      dialogVisible: false,
      form: {
        name: "",
        region: "",
        date1: "",
        date2: "",
        delivery: false,
        type: [],
        resource: "",
        desc: "",
      },

      mtar_upload_mode: "2",
      select_app_show: false,
      checkboxGroup1: [],
      cities: cityOptions,
      icaClientNode_show: false,
      server_show: false,
      workSpace_show: false,
      ica_client_node_value: "",
      server_value: "",
      work_space_value: "",
      extension_mar_show: false,
      yaml_value: "",
      input_api_endpoint: "api.cf.eu12.hana.ondemand",
      org_name: "ica_fun_eu12_org",
      space_name: "prov_eu12_acfun002",

      active: 0,
      activeIndex: "1",
      activeIndex2: "1",
      options: [
        {
          value: "Paired-end reads",
          label: "Paired-end reads",
        },
        {
          value: "Single-end read or fastq-joined file",
          label: "Single-end read or fastq-joined file",
        },
      ],
      // uploadUrl: "/api/upload/uploadFile",
      uploadUrl: "http://localhost:9999/api/upload/uploadFile",
      acceptGZ: ".gz",
      acceptXLSX: ".xlsx",
      //文件上传列表
      GZFileList: [],
      XLSXFileList: [],
      email: "",
    };
  },
  methods: {
    welcome() {
      this.$message({
        showClose: true,
        message: "WelCome To Use PeiQi",
      });
    },

    select_app(index) {
      var tmp;
      if (index == 0) {
        tmp = this.icaClientNode_show;
        this.icaClientNode_show = !tmp;
      } else if (index == 1) {
        tmp = this.server_show;
        this.server_show = !tmp;
      } else if (index == 2) {
        tmp = this.workSpace_show;
        this.workSpace_show = !tmp;
      }

      console.log(this.icaClientNode_show);
      console.log(this.server_show);
      console.log(this.workSpace_show);
    },

    handleCloseDialog(done) {
      this.$confirm("confirm to close ?","Tips",{
        confirmButtonText: 'confirm',
        cancelButtonText: 'cancel'
      })
        .then((_) => {
          this.dialogVisible = false;
          this.mtar_upload_mode = "2";
        })
        .catch((_) => {});
    },

    // 点击步骤
    next() {
      if (this.active++ > 2) this.active = 0;
    },

    handleSelect() {},
    //下载xlsx 样例文件
    downloadMtarExtensionFile() {
      var that = this;
      that.axios
        .post(
          "/download/XLSXExampleFile",
          { fileId: 123 },
          { responseType: "blob" } // 设置responseType对象格式为 blob:
        )
        .then((res) => {
          console.log(res);
          let blob = new Blob([res.data], {
            type: "application/octet-stream",
          }); // 获取请求返回的response对象中的blob 设置文件类型

          let url = window.URL.createObjectURL(blob); // 创建一个临时的url指向blob对象
          let a = document.createElement("a");
          a.href = url;
          a.download = "text.xlsx";
          a.click();
          window.URL.revokeObjectURL(url); //释放blob对象
        });
    },

    //下载 gz样例文件
    downloadGZFile() {
      var that = this;
      that.axios
        .post(
          "/download/GZExampleFile",
          { fileId: 123 },
          { responseType: "blob" } // 设置responseType对象格式为 blob:
        )
        .then((res) => {
          console.log(res);
          let blob = new Blob([res.data], {
            type: "application/octet-stream",
          }); // 获取请求返回的response对象中的blob 设置文件类型

          let url = window.URL.createObjectURL(blob); // 创建一个临时的url指向blob对象
          let a = document.createElement("a");
          a.href = url;
          a.download = "test.fq.gz";
          a.click();
          window.URL.revokeObjectURL(url); //释放blob对象
        });
    },
    handleExceed(files, fileList) {
      this.$message.warning(`you can only upload one file `);
    },
    beforeGZRemove(file, fileList) {
      this.GZFileList.pop();
      this.$message({
        type: "success",
        message: "Delete Succsssfully !!",
      });
    },
    onGZSuccess(res) {
      this.$message.success("upload successfully");
      this.GZFileList.push(res.data);
    },
    onError(res) {
      this.$message("fail to upload file , plz try again !");
    },
    submitGZUpload() {
      var that = this;
      that.$nextTick(() => {
        this.$refs.GZUpload.submit();
        this.active = 1;
      });
    },
    // second upload button
    onXLSXSuccess(res) {
      this.$message.success("upload successfully");
      this.XLSXFileList.push(res.data);
    },
    beforeXLSXRemove() {
      this.XLSXFileList.pop();
      this.$message({
        type: "success",
        message: "Delete Succsssfully !!",
      });
    },
    submitXLSXUpload() {
      var that = this;
      that.$nextTick(() => {
        this.$refs.XLSXUpload.submit();
        this.active = 2;
      });
    },

    enterEmail() {
      console.log(this.yaml_value);
      // this.$prompt("Please enter Email", "Tips", {
      //   confirmButtonText: "Confirm",
      //   cancelButtonText: "Cancel",
      //   inputPattern:
      //     /[\w!#$%&'*+/=?^_`{|}~-]+(?:\.[\w!#$%&'*+/=?^_`{|}~-]+)*@(?:[\w](?:[\w-]*[\w])?\.)+[\w](?:[\w-]*[\w])?/,
      //   inputErrorMessage: "Email is not correct",
      // })
      //   .then(({ value }) => {
      //     this.$message({
      //       type: "success",
      //       message: "Your Email is : " + value,
      //     });
      //     this.email = value;
      //     this.submitAction();
      //   })
      //   .catch(() => {
      //     this.$message({
      //       type: "info",
      //       message: "Cancel Enter",
      //     });
      //   });
    },

    submitAction() {
      if (this.GZFileList.length == 0) {
        this.$message.warning("gz file can not be empty !");
      } else if (this.XLSXFileList.length == 0) {
        this.$message.warning("xlsx file can not be empty !");
      } else {
        // const qs = require('qs');
        var that = this;
        var param = {
          GZFileList: this.GZFileList,
          XLSXFileList: this.XLSXFileList,
          email: this.email,
        };
        that
          .axios({
            method: "post",
            url: "/business/submit",
            data: JSON.stringify(param),
            headers: {
              "Content-Type": "application/json;charset=UTF-8",
            },
          })
          .then((res) => {
            if (res.data.code == 200) {
              that.$message.success(
                "submit successfully! , Plz wait for some time .You will receive Email in the later time. Check on your box! "
              );
              this.active = 3;
              setTimeout(function () {
                location.reload();
              }, 2000);
            }
          });
      }
    },
  },

  watch: {
    mtar_upload_mode() {
      if (this.mtar_upload_mode == "0") {
        this.select_app_show = true;
      }
      if (this.mtar_upload_mode != "0") {
        this.select_app_show = false;
        this.extension_mar_show = false;
      }
      if(this.mtar_upload_mode == "1"){
        this.dialogVisible = true;
        this.extension_mar_show = false;
        this.ica_client_node_value = "";
        this.server_value = "";
        this.work_space_value = "";
      }
    },

    ica_client_node_value() {
      if (this.ica_client_node_value != "") {
        this.extension_mar_show = true;
      }
      if (
        this.ica_client_node_value === "" &&
        this.server_value === "" &&
        this.work_space_value === ""
      ) {
        this.extension_mar_show = false;
      }
    },
    server_value() {
      if (this.server_value != "") {
        this.extension_mar_show = true;
      }
      if (
        this.ica_client_node_value === "" &&
        this.server_value === "" &&
        this.work_space_value === ""
      ) {
        this.extension_mar_show = false;
      }
    },
    work_space_value() {
      if (this.work_space_value != "") {
        this.extension_mar_show = true;
      }
      if (
        this.ica_client_node_value === "" &&
        this.server_value === "" &&
        this.work_space_value === ""
      ) {
        this.extension_mar_show = false;
      }
    },
  },
  name: "YamlEditorDemo",
  components: {
    YamlEditor,
  },
};
</script>

<style lang="less" scoped>
.gene_main {
  // width: 80%;
  //   height: 100%;
  // background-color: #85ffbd;
  //   background-image: linear-gradient(45deg, #85ffbd 0%, #fffb7d 100%);
  padding-bottom: 100px;
  .el-menu-demo {
    // background-color: #c0b1b1;
    .nav_first {
      font-size: 20px;
      padding-left: 75px;
      padding-right: 45px;
      color: #222121;
    }
  }

  .gene_body {
    background-color: #f9fafc;
    margin-left: 300px;
    width: 60%;
    padding-left: 18px;
    .font_style {
      h2 {
        margin-top: 0;
        padding-top: 10px;
      }
      .p_all {
        p {
          display: block;
          margin-block-start: 1em;
          margin-block-end: 1em;
          margin-inline-start: 0px;
          margin-inline-end: 0px;
          font-family: "Open Sans", "Helvetica Neue", Helvetica, Arial,
            sans-serif;
          font-size: 14px;
          line-height: 20px;
          color: #666;
        }
      }
    }

    .gene_panel {
      //   border: 1px solid red;
      .gene_container {
      }
      .gene_main {
        // border: 1px solid blue;
        .panel_all {
          //   border: 1px solid blue;
          padding-top: 10px;
          padding-left: 20px;
          padding-bottom: 24px;
          .panel_title {
            border-bottom: 1px solid #e5e5e5;
          }
          .panel_first_content {
            .content_subTitle {
              a {
                margin-left: 20px;
              }
            }

            padding-left: 14px;
            .content_select {
              // text-align: center;
              .select_btn:not(:first-child) {
                padding-left: 90px;
              }
            }
            .content_file_upload {
              margin-top: 10px;
              // padding-top: 20px;
              .content_upload_gz {
                .el-upload__tip {
                  margin-left: 14px;
                }
              }
            }
          }
          .panel_sec_content {
            padding-left: 14px;
            .content_subTitle {
              a {
                margin-left: 10px;
              }
            }
            .content_input {
              .content_api_endpoint {
                width: 50%;
                .sub-title {
                  margin-top: 10px;
                  margin-bottom: 10px;
                  font-size: 14px;
                  color: #8492a6;
                }
              }
              .content_org_space {
                .sub-title {
                  margin-top: 10px;
                  margin-bottom: 10px;
                  font-size: 14px;
                  color: #8492a6;
                }
              }
            }
            .content_mtar_file_upload {
              margin-top: 20px;
              .el-col {
                text-align: left;
              }
            }

            .content_upload_xlsx {
              .el-upload__tip {
                margin-left: 14px;
              }
            }
            .editor-container {
              padding-top: 20px;
              position: relative;
              width: 80%;
              height: 100%;
            }
            .submit_button {
              margin-top: 30px;
              text-align: center;
            }
          }
        }
      }
    }
  }

  .float_steps {
    .float_form {
      margin-left: 15px;
    }
    // border: #222121 solid 1px;
    background-color: #e4e7eb;
    width: 200px;
    height: 400px;
    position: fixed;
    float: right;
    left: 50%;
    top: 27%;
    // z-index: 500;
    margin-left: 630px;
    padding-bottom: 25px;
  }
}

.second_panel_tips {
  text-align: center;
  color: red;
}

.second_panel_submit_button {
  text-align: center;
}

.second_panel_pic {
  text-align: center;
}
.second_panel_pic2 {
  text-align: center;
  margin-top: 50px;
}

.el-row {
  margin-bottom: 20px;
  &:last-child {
    margin-bottom: 0;
  }
}
.el-col {
  border-radius: 4px;
}
.bg-purple-dark {
  background: #99a9bf;
}
.bg-purple {
  background: #d3dce6;
}
.bg-purple-light {
  background: #e5e9f2;
}
.grid-content {
  border-radius: 4px;
  min-height: 36px;
}
.row-bg {
  padding: 10px 0;
  background-color: #f9fafc;
}
</style>



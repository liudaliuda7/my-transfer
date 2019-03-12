<template>
    <div>
        <div class="transfer" :style="{width,height}">
            <template v-if="mode == 'transfer'">
              <!-- 左侧穿梭框 原料框 -->
              <div class="transfer-left">
                <h3 class="transfer-title">
                  <el-checkbox :indeterminate="from_is_indeterminate" v-model="from_check_all" @change='fromAllBoxChange'></el-checkbox>
                  <span>{{fromTitle}}</span>
                </h3>
                <!-- 内容区 -->
                <div class="transfer-main">
                  <!-- <slot name="from"></slot> -->
                  <el-input v-if="filter" :placeholder="placeholder" v-model="filterFrom" size="small" class="filter-tree">
                  </el-input>
                  <el-tree ref='from-tree' :data="self_from_data" show-checkbox :node-key="node_key" @check='fromTreeChecked' :default-expanded-keys="from_expanded_keys" :props="defaultProps" :filter-node-method="filterNodeFrom" :default-expand-all="openAll" :render-content='renderContent' :default-checked-keys="defaultCheckedKeys">
                  </el-tree>
                  <slot name="left-footer"></slot>
                </div>
              </div>
              <!-- 穿梭区 按钮框 -->
              <div class="transfer-center">
                <template v-if='button_text'>
                  <p class="transfer-center-item">
                    <el-button type="primary" @click="addToAims" :disabled="from_disabled">
                      {{fromButton || '添加'}}
                      <i class="el-icon-arrow-right"></i>
                    </el-button>
                  </p>
                  <p class="transfer-center-item">
                    <el-button type="primary" @click='removeToSource' :disabled="to_disabled" icon="el-icon-arrow-left">{{toButton || '移除'}}</el-button>
                  </p>
                </template>
                <template v-else>
                  <p class="transfer-center-item">
                    <el-button type="primary" @click="addToAims" icon="el-icon-arrow-right" circle :disabled="from_disabled"></el-button>
                  </p>
                  <p class="transfer-center-item">
                    <el-button type="primary" @click='removeToSource' :disabled="to_disabled" icon="el-icon-arrow-left" circle></el-button>
                  </p>
                </template>
              </div>
              <!-- 右侧穿梭框 目标框 -->
              <div class="transfer-right">
                <h3 class="transfer-title">
                  <el-checkbox :indeterminate="to_is_indeterminate" v-model="to_check_all" @change="toAllBoxChange"></el-checkbox>
                  <span>{{toTitle}}</span>
                </h3>
                <!-- 内容区 -->
                <div class="transfer-main">
                  <!-- <slot name='to'></slot> -->
                  <el-input v-if="filter" :placeholder="placeholder" v-model="filterTo" size="small" class="filter-tree">
                  </el-input>
                  <el-tree slot='to' ref='to-tree' :data="self_to_data" show-checkbox :node-key="node_key" @check='toTreeChecked' :default-expanded-keys="to_expanded_keys" :props="defaultProps" :filter-node-method="filterNodeTo" :default-expand-all="openAll" :render-content='renderContent'>
                  </el-tree>
                  <slot name="right-footer"></slot>
                </div>
              </div>
            </template>
        </div>
        <el-input v-model="input" placeholder="请输入内容"></el-input>
        <div></div>
    </div>
</template>

<script>
export default {
    name: "transfer",
    data() {
        return {
            
        }
    },
}
</script>
<style>

</style>

<template>
  <div class="hello">
    <!-- 顶端Nav -->
    <van-row>
      <van-nav-bar
        title="云海流智能系统"
        :left-text="leftText"
        right-text=". . ."
        left-arrow
        @click-left="onClickLeft"
        @click-right="onClickRight"
      />
    </van-row>
    <van-row type="flex" justify="center">
      <van-col :span="2"></van-col>
      <van-col :span="20">
        <van-tabs v-model="step" color="#1677FF">
          <van-tab title="类型选择">
            <!-- 三个产品类型选项 -->
            <van-radio-group v-model="productType">
              <van-cell-group>
                <van-cell title="名片" clickable @click="radio = 'Card'">
                  <template #right-icon>
                    <van-radio name="Card" />
                  </template>
                </van-cell>
                <van-cell title="名片盒" clickable @click="radio = 'Box'">
                  <template #right-icon>
                    <van-radio name="Box" />
                  </template>
                </van-cell>
                <van-cell title="钥匙扣" clickable @click="radio = 'KeyChain'">
                  <template #right-icon>
                    <van-radio name="KeyChain" />
                  </template>
                </van-cell>
              </van-cell-group>
            </van-radio-group>
            <!-- 确认按钮 -->
            <van-row type="flex" justify="center">
              <van-button type="info" @click="onClickConfirmProductType">
                确认
              </van-button>
            </van-row>
          </van-tab>
          <van-tab title="信息输入">
            <van-form @submit="onSubmit">
              <van-field
                v-model="username"
                name="用户名"
                label="用户名"
                placeholder="用户名"
                :rules="[{ required: true, message: '请填写用户名' }]"
              />
              <van-field
                v-model="password"
                type="password"
                name="密码"
                label="密码"
                placeholder="密码"
                :rules="[{ required: true, message: '请填写密码' }]"
              />
            </van-form>

            <!-- 确认按钮 -->
            <van-row type="flex" justify="center">
              <van-button type="info" @click="onClickConfirmProductInfo">
                确认
              </van-button>
            </van-row>
          </van-tab>
          <van-tab title="工单生成">
            <!-- 确认按钮 -->
            <van-row type="flex" justify="center">
              <van-button type="info" @click="onClickGenerateOrder">
                生成工单
              </van-button>
            </van-row>
          </van-tab>
        </van-tabs>
      </van-col>
      <van-col :span="2"></van-col>
    </van-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      value: "Card",
      step: 0,
      leftText: "",
      productType: "Card",
      username: "drop",
      password: "TQcpsPassword",
    };
  },
  methods: {
    onClickLeft() {
      this.$toast("返回");
    },
    onClickRight() {
      this.$toast("按钮");
    },
    onClickConfirmProductType() {
      this.$dialog
        .confirm({
          title: "标题",
          message: "弹窗内容",
        })
        .then(() => {
          // on confirm
        })
        .catch(() => {
          // on cancel
        });
    },

    onClickConfirmProductInfo() {
      this.$dialog
        .confirm({
          title: "标题",
          message: "弹窗内容",
        })
        .then(() => {
          // on confirm
        })
        .catch(() => {
          // on cancel
        });
    },

    onClickGenerateOrder() {
      this.$dialog
        .confirm({
          title: "标题",
          message: "弹窗内容",
        })
        .then(async () => {
          // on confirm
          const postData = {
            cmd: "create_order",
            goods_type: "名片",
            user_openid: "user_name",
            draw_info: {
              body_name: "body_name",
              cor_name: "cor_name",
              cor_addr: "cor_addr",
              cor_phone: "cor_phone",
              cor_email: "cor_email",
            },
          };
          const { data: res } = await this.$http.post(
            "http://127.0.0.1/upload",
            postData
          );
          console.log(res);
        })
        .catch(() => {
          // on cancel
        });
    },

    // 提交表单
    onSubmit(values) {
      console.log("submit", values);
    },
  },
};
</script>

<style scoped></style>

<template>
  <!-- <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
  </div> -->
  <section class="ftco-section">
    <div class="container">
      <div class="row justify-content-center">
        <div class="col-md-12">
          <div class="wrapper">
            <div class="row no-gutters">
              <div
                class="
                  col-lg-8 col-md-7
                  order-md-last
                  d-flex
                  align-items-stretch
                "
              >
                <div class="contact-wrap w-100 p-md-5 p-4">
                  <h3 class="mb-4">
                    愛生．計劃 一籃子捐款<br />Give-back Campaign Bundle
                    Donation
                  </h3>
                  <form
                    id="contactForm"
                    name="contactForm"
                    class="contactForm"
                    autocomplete="off"
                    @submit.prevent="submit"
                  >
                    <div class="row">
                      <div class="col-md-6">
                        <div class="form-group">
                          <label class="label" for="name">全名 Full Name</label>
                          <input
                            type="text"
                            class="form-control"
                            name="name"
                            id="name"
                            placeholder="Name"
                            required
                            v-model="name"
                          />
                        </div>
                      </div>
                      <div class="col-md-6">
                        <div class="form-group">
                          <label class="label" for="email"
                            >電郵地址 Email Address</label
                          >
                          <input
                            type="email"
                            class="form-control"
                            name="email"
                            id="email"
                            placeholder="Email"
                            required
                            v-model="email"
                          />
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form-group">
                          <label class="label" for="amount"
                            >捐款金額 Donation Amount</label
                          >
                          <div class="custom-control custom-radio">
                            <input
                              type="radio"
                              id="m100"
                              name="amount"
                              class="custom-control-input"
                              required
                              value="100"
                              v-model="amount"
                            />
                            <label class="custom-control-label" for="m100"
                              >HK$ 100.00 x 6 個月（6 months）</label
                            >
                          </div>
                          <div class="custom-control custom-radio">
                            <input
                              type="radio"
                              id="m300"
                              name="amount"
                              class="custom-control-input"
                              required
                              value="300"
                              v-model="amount"
                            />
                            <label class="custom-control-label" for="m300"
                              >HK$ 300.00 x 6 個月（6 months）</label
                            >
                          </div>
                          <div class="custom-control custom-radio">
                            <input
                              type="radio"
                              id="m500"
                              name="amount"
                              class="custom-control-input"
                              required
                              value="500"
                              v-model="amount"
                            />
                            <label class="custom-control-label" for="m500"
                              >HK$ 500.00 x 6 個月（6 months）</label
                            >
                          </div>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form-group">
                          <label class="label" for="#"
                            >條款及細則 Terms and Conditions</label
                          >
                          <div class="custom-control custom-checkbox">
                            <input
                              type="checkbox"
                              class="custom-control-input"
                              id="acceptTnC"
                              :disabled="isLoading"
                              required
                            />
                            <label class="custom-control-label" for="acceptTnC"
                              >我同意 Givemunity 的條款及細則，並同意 Givemunity
                              及有關慈善單位將會透過我提供的聯絡方法(包括姓名及電郵地址)，為我提供通訊、籌募、義工招募及相關資訊，以及用作收集意見之用途。<br />I
                              agree Givemunity's Terms and Conditions, and I
                              agree that Givemunity and the charity units may
                              use my contact information (name and email
                              address) for the purpose of communications,
                              fundraising, volunteer recruitment and survey
                              administration.</label
                            >
                          </div>
                        </div>
                      </div>
                      <div class="col-md-12">
                        <div class="form-group">
                          <button class="btn btn-primary">
                            前往付款 Continue to pay {{ loading }}
                          </button>
                          <div class="submitting"></div>
                        </div>
                      </div>
                    </div>
                  </form>
                </div>
              </div>
              <div class="col-lg-4 col-md-5 d-flex align-items-stretch">
                <div class="info-wrap bg-primary w-100 p-md-5 p-4">
                  <h3>Givemunity</h3>
                  <p class="mb-4">
                    一個專注公益及慈善的平台<br />
                    Connect Small Social Units With Big Heart Donors
                  </p>
                  <p class="mb-4">
                    愛生．計劃為 Givemunity
                    捐款平台的試驗計劃，為期六個月，旨在為十間慈善機構籌得穩定的恆常善款。<br />
                    Give-back Campaign is a trial program of Givemunity's
                    Donation Platform. The campaign lasts for 6 months, and is
                    targeted to raise funding for 10 charity units.
                  </p>
                  <div class="dbox w-100 d-flex align-items-center">
                    <div
                      class="
                        icon
                        d-flex
                        align-items-center
                        justify-content-center
                      "
                    >
                      <span class="fa fa-paper-plane"></span>
                    </div>
                    <div class="text pl-3">
                      <p>
                        <span>Email: </span>
                        <a href="mailto:givemunity@gmail.com"
                          >givemunity@gmail.com</a
                        >
                      </p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import { onMounted, defineComponent } from "vue";
import axios from "axios";

export default defineComponent({
  name: "Home",
  data() {
    return {
      name: "",
      email: "",
      amount: "",
      isLoading: false,
      loading: "",
    };
  },
  setup() {
    // mounted
    onMounted(() => {
      document.title =
        "愛生．計劃 一籃子捐款 Give-back Campaign Bundle Donation - Givemunity";
    });
  },
  methods: {
    submit() {
      console.log(this.name);
      console.log(this.email);
      console.log(this.amount);
      console.log(process.env.VUE_APP_API_BASE_URL);
      this.isLoading = true;
      this.loading = "- Loading... 處理中...";
      axios
        .post(
          "/poc/v1/donor_response",
          {
            name: this.name,
            email: this.email,
            amount: parseInt(this.amount),
          },
          {
            baseURL: process.env.VUE_APP_API_BASE_URL,
          }
        )
        .then(function (response) {
          console.log(response);
          window.location.href = response.data.payment_link;
        })
        .catch(function (error) {
          console.log(error);
        });
    },
  },
});
</script>
<style scoped>
@import "../assets/style.css";
</style>

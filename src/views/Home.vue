<template>
  <div class="home">
    <div class="container">
      <!-- Ticketboy logo image -->
      <a href=""
        ><img
          src="@/assets/tboy.png"
          alt="Company Logo"
          translate="no"
          class="home__coy__logo"
      /></a>

      <div class="col col-md-5">
        <div class="home__cont">
          <h1 class="home__header mb-0">
            Your <span class="home__tickets__text">tickets</span> to
          </h1>
          <h1 class="home__header">experience live.</h1>
          <p class="home__header__text">
            We’re transforming the way fans buy and sell tickets to their
            favourite live events in Africa. Get instant and verified tickets
            anywhere, anytime.
          </p>
          <div class="home__buttons__container">
            <div>
              <!-- Element UI Form and Input start -->
              <el-form
                :model="dynamicValidateForm"
                ref="dynamicValidateForm"
                label-width="120px"
                class="demo-dynamic"
              >
                <el-form-item
                  prop="email"
                  placeholder="Enter your email address"
                  label=""
                  :rules="[
                    {
                      required: true,
                      message: 'Please input email address',
                      trigger: 'blur',
                    },
                    {
                      type: 'email',
                      message: 'Please input correct email address',
                      trigger: ['blur', 'change'],
                    },
                  ]"
                >
                  <el-input
                    v-model="dynamicValidateForm.email"
                    placeholder="Enter your email address"
                    class="home__input"
                  ></el-input>
                </el-form-item>
              </el-form>
              <!-- Element UI Form and Input end -->
            </div>

            <!-- Submit Button -->
            <div>
              <button
                class="btn w-100 home__button__blue"
                @click="submitForm('dynamicValidateForm')"
                id="getAccessBtn"
              >
                Get Early Access
              </button>
            </div>
            <!-- Submit Button -->
          </div>
        </div>
        <!-- Desktop Images -->
        <div class="home__boy__group">
          <img
            src="@/assets/Vector(1).png"
            alt="TickeyBoy"
            class="home__vector"
          />

          <img src="@/assets/man.png" alt="TicketBoy" class="home__dj-image" />
        </div>

        <!-- Mobile foot arranf=ged images -->
        <div class="home__mobile__images">
          <img src="@/assets/mobile-man (1).png" alt="" class="img-one" />
          <img src="@/assets/mobile-man (2).png" alt="" class="img-two" />
        </div>
      </div>

      <!-- Contrast divs -->
      <div class="contrast contrast-one"></div>
      <div class="contrast contrast-two"></div>
    </div>
  </div>
</template>



  <script type="text/javascript" src="https://cdn.jsdelivr.net/npm/emailjs-com@2/dist/email.min.js"></script>
 <script type="text/javascript">
(function () {
  emailjs.init("user_clplcO5e1dK5gp2xPVmAz");
})();
</script>



<script>
export default {
  data() {
    return {
      dynamicValidateForm: {
        email: "",
      },
    };
  },
  methods: {
    submitForm(formName) {

      // Validate Form
      this.$refs[formName].validate((valid) => {
        if (valid) {


          // Try function to send mail
          try {
            
            // Getting button to manipulate textContent
            const btnGetAccess = document.getElementById("getAccessBtn");
            btnGetAccess.textContent = "Requesting....";

            // TempParams Defined to specify user email
            let tempParams = {
              user_email: this.dynamicValidateForm.email,
            };

            // ServiceId and templateId defined and assigned
            const serviceID = "service_66b4c6r";
            const templateID = "template_koxidqv";

            // Send mail function
            emailjs.send(serviceID, templateID, tempParams).then(
              () => {
                btnGetAccess.textContent = "Get Early Access";
                this.dynamicValidateForm.email = "";

                // Trigger success message
                this.$message({
                  message:
                    "Congrats, You have been added to TicketBoy's waiting list.",
                  type: "success",
                });
              },

              // catch error
              (err) => {
                // set default
                btnGetAccess.textContent = "Get Early Access";
                this.dynamicValidateForm.email = "";
                alert(JSON.stringify(err));
              }
            );
          } catch (error) {
            console.log(error);
          }
        } else {
          // Catch submit button error
          console.log("error submit!!");
          return false;
        }
      });
    },
  },
};
</script>

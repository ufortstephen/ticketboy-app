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
          <h1 class="home__header">
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
              <el-input
                placeholder="Enter your Email Address"
                v-model="input"
                clearable
                class="home__input"
              >
              </el-input>
            </div>
            <div>
              <button class="btn w-100 home__button__blue">
                Get Early Access
              </button>
            </div>
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

<script>
// @ is an alias to /src

export default {
  name: "Home",
  data() {
    return {
      input: "",
    };
  },
};
</script>

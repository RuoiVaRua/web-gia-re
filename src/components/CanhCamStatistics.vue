<template>
  <section class="outstanding-numbers-section">
    <div class="container">
      <div class="heading-container">
        <h3 class="heading animated-text">Outstanding Numbers</h3>
      </div>
      <div class="description-container">
        <p class="description animated-text">
          CanhCam is the leading web design agency in Vietnam. Our dedicated and innovative
          team is committed to providing website solutions that surpass customer’s expectations.
        </p>
      </div>
    </div>
    <div class="numbers-container">
      <div class="number-item">
        <div class="component-2">
          <span class="number animated-text">{{ number1 }}{{ suffixes[0] }}</span>
        </div>
        <div class="margin">
          <div class="container-inner">
            <p class="text animated-text">Years of experience</p>
          </div>
        </div>
      </div>
      <div class="number-item">
        <div class="component-2">
          <span class="number animated-text">{{ number2 }}{{ suffixes[1] }}</span>
        </div>
        <div class="margin">
          <div class="container-inner">
            <p class="text animated-text">
              Saved cost for business<br />
              operation
            </p>
          </div>
        </div>
      </div>
      <div class="number-item">
        <div class="component-2">
          <span class="number animated-text">{{ number3 }}{{ suffixes[2] }}</span>
        </div>
        <div class="margin">
          <div class="container-inner">
            <p class="text animated-text">
              Commitment rate (in terms of<br />
              quality, time and cost)
            </p>
          </div>
        </div>
      </div>
      <div class="number-item">
        <div class="component-2">
          <span class="number animated-text">{{ number4 }}{{ suffixes[3] }}</span>
        </div>
        <div class="margin">
          <div class="container-inner">
            <p class="text animated-text">Projects</p>
          </div>
        </div>
      </div>
      <div class="number-item">
        <div class="component-2">
          <span class="number animated-text">{{ number5 }}{{ suffixes[4] }}</span>
        </div>
        <div class="margin">
          <div class="container-inner">
            <p class="text animated-text">Projects</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted, type Ref } from 'vue';

const number1: Ref<number> = ref(0);
const number2: Ref<number> = ref(0);
const number3: Ref<number> = ref(0);
const number4: Ref<number> = ref(0);
const number5: Ref<number> = ref(0); // This one remains 0

const targetValues: number[] = [100, 24, 24, 600, 0];
const suffixes: string[] = [' +', ' %', ' %', ' +', ' +'];
const animationDuration: number = 3000; // milliseconds

let animatedNumbersObserver: IntersectionObserver | null = null;
let numbersContainerObserver: IntersectionObserver | null = null;
let animationStarted: boolean = false;

const animateNumber = (refVar: Ref<number>, target: number, duration: number) => {
  if (target === 0) {
    refVar.value = 0;
    return;
  }

  const startValue = refVar.value;
  const startTime = performance.now();

  const update = (currentTime: DOMHighResTimeStamp) => {
    const elapsedTime = currentTime - startTime;
    const progress = Math.min(elapsedTime / duration, 1);
    refVar.value = Math.floor(startValue + (target - startValue) * progress);

    if (progress < 1) {
      requestAnimationFrame(update);
    }
  };

  requestAnimationFrame(update);
};

onMounted(() => {
  const animatedElements = document.querySelectorAll('.animated-text');
  const numbersContainer = document.querySelector('.numbers-container');

  animatedNumbersObserver = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add('is-visible');
        } else {
          entry.target.classList.remove('is-visible');
        }
      });
    },
    { threshold: 0.1 }
  );

  animatedElements.forEach((item) => {
    animatedNumbersObserver?.observe(item);
  });

  if (numbersContainer) {
    numbersContainerObserver = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting && entry.intersectionRatio === 1 && !animationStarted) {
            animationStarted = true;
            animateNumber(number1, targetValues[0], animationDuration);
            animateNumber(number2, targetValues[1], animationDuration);
            animateNumber(number3, targetValues[2], animationDuration);
            animateNumber(number4, targetValues[3], animationDuration);
            // number5 remains 0, no animation needed
            numbersContainerObserver?.unobserve(entry.target); // Stop observing after animation starts
          }
        });
      },
      { threshold: 1.0 } // Trigger when 100% of the item is visible
    );
    numbersContainerObserver.observe(numbersContainer);
  }
});

onUnmounted(() => {
  animatedNumbersObserver?.disconnect();
  numbersContainerObserver?.disconnect();
});
</script>

<style lang="scss" scoped>
.outstanding-numbers-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 60px;
  padding: 80px 0px;
  width: 100%;
  background: radial-gradient(
    circle at 99.99999868324028% -49.49999936780334%,
    #F73936 0%,
    #B41C3E 100%
  );

  .animated-text {
    opacity: 0;
    transform: translateY(50px);
    transition: opacity 0.4s ease-out, transform 0.4s ease-out;

    &.text, &.number {
      transform: translateY(100px);
    }

    &.is-visible {
      opacity: 1;
      transform: translateY(0);
    }
  }

  .container {
    display: flex;
    flex-direction: column;
    gap: 20px;
    width: 960px;
    text-align: center;

    .heading-container {
      display: flex;
      flex-direction: column;
      align-self: stretch;
      padding-bottom: 8px;

      .heading {
        font-family: 'Inter', sans-serif;
        font-weight: 700;
        font-size: 46.5px;
        line-height: 1.29;
        color: #FFFFFF;
        text-align: center;
        transition-delay: 0.2s; /* Delay cho heading */
      }
    }

    .description-container {
      display: flex;
      flex-direction: column;
      align-self: stretch;
      padding-bottom: 124px;

      .description {
        font-family: 'Inter', sans-serif;
        font-weight: 200;
        font-size: 22.875px;
        line-height: 1.57;
        color: #FFFFFF;
        text-align: center;
        transition-delay: 0.4s; /* Delay cho description */
      }
    }
  }

  .numbers-container {
    display: flex;
    flex-direction: row;
    justify-content: center;
    width: 1279.98px;
    flex-wrap: wrap; /* Để đảm bảo responsive */

    .number-item {
      display: flex;
      flex-direction: column;
      align-self: stretch;
      gap: 8px;
      padding: 32px 20px;
      flex: 1; /* Để các item chia đều không gian */
      min-width: 250px; /* Đảm bảo các item không quá nhỏ */

      @for $i from 1 through 5 { // Có 5 number-item
        &:nth-child(#{$i}) {
          .number {
            transition-delay: #{(0.6 + ($i - 1) * 0.2)}s; // Delay cho number
          }
          .text {
            transition-delay: #{(0.8 + ($i - 1) * 0.2)}s; // Delay cho text
          }
        }
      }

      .component-2 {
        display: flex;
        flex-direction: column;
        align-items: center;
        align-self: stretch;

        .number {
          font-family: 'Inter', sans-serif;
          font-weight: 700;
          font-size: 56.75px;
          line-height: 0.84;
          color: #FFFFFF;
          text-align: center;
          -webkit-text-stroke: 2px #FFFFFF; /* Stroke cho text */
          text-stroke: 2px #FFFFFF;
        }
      }

      .margin {
        display: flex;
        flex-direction: column;
        align-self: stretch;
        padding-top: 20px;

        .container-inner {
          display: flex;
          flex-direction: column;
          align-items: center;
          align-self: stretch;

          .text {
            font-family: 'Inter', sans-serif;
            font-weight: 700;
            font-size: 19.375px; /* Sử dụng kích thước chung cho các text */
            line-height: 1.55; /* Sử dụng line-height chung */
            color: #FFFFFF;
            text-align: center;
          }
        }
      }
    }
  }
}

/* Responsive adjustments */
@media (max-width: 1280px) {
  .outstanding-numbers-section {
    .container {
      width: 100%;
      padding: 0 20px;
    }
    .numbers-container {
      width: 100%;
      padding: 0 20px;
    }
  }
}

@media (max-width: 768px) {
  .outstanding-numbers-section {
    gap: 40px;
    padding: 60px 0px;

    .container {
      .heading-container {
        .heading {
          font-size: 36px;
        }
      }
      .description-container {
        padding-bottom: 60px;
        .description {
          font-size: 18px;
        }
      }
    }

    .numbers-container {
      flex-direction: column;
      align-items: center;

      .number-item {
        min-width: unset;
        width: 100%;
        max-width: 300px; /* Giới hạn chiều rộng trên mobile */
      }
    }
  }
}

@media (max-width: 480px) {
  .outstanding-numbers-section {
    .container {
      .heading-container {
        .heading {
          font-size: 28px;
        }
      }
      .description-container {
        .description {
          font-size: 16px;
        }
      }
    }
    .numbers-container {
      .number-item {
        .component-2 {
          .number {
            font-size: 48px;
          }
        }
        .margin {
          .container-inner {
            .text {
              font-size: 16px;
            }
          }
        }
      }
    }
  }
}
</style>

<template>
  <container class="aboutme">
    <Title
      :text="aboutMeContent.title"
      component="h2"
    />
    <div class="row">
      <div class="col-6 imageSec">
        <div class="shadow">
          <span>{{aboutMeContent.image[0].metadata.description}}</span>
        </div>
        <img
          class="groupDot"
          src="/img/groupDot.svg"
          alt
        />
        <div class="img">
          <img
            :src="aboutMeContent.image[0].url"
            :alt="aboutMeContent.image[0].metadata.description"
          />
        </div>
        <SocialMedia :socialMedia="pageData.socialMedia.iv[0]" />
        <!-- <div class="shadow"></div> -->
      </div>
      <div class="col-6 content">
        <div class="data">
          <p
            class="textContent"
            v-for="content in aboutMeContent.textContent"
          >{{content}}</p>
          <div class="metaData">
            <ul>
              <li v-for="key in Object.keys(aboutMeContent.metaData)">
                <img
                  :src="'/img/'+key+'.svg'"
                  :alt="key"
                />
                {{aboutMeContent.metaData[key]}}
              </li>
            </ul>
          </div>
          <button
            class="btn arrow"
            @click="$scrollTo('.myskills', { offset: 80 })"
          >{{aboutMeContent.buttonText}}</button>
        </div>
      </div>
    </div>

    <div class="dotUtils">
      <Multiply :style="{
		 top: '34px',
		 left: '400px',
		 zIndex: '-1'
	 }" />
      <Multiply :style="{
		 top: '650px',
		 left: '626px',
		 zIndex: '-1'
	 }" />
      <Multiply :style="{
		 top: '850px',
		 left: '1176px',
		 zIndex: '-1'
	 }" />

      <div
        class="dot"
        :style="{
		 top: '80px',
		 left: '506px',
		 zIndex: '-1'
	 }"
      ></div>
      <div
        class="dot b"
        :style="{
		 top: '770px',
		 left: '166px',
		 zIndex: '-1'
	 }"
      ></div>
      <div
        class="dot a"
        :style="{
		 top: '890px',
		 left: '756px',
		 zIndex: '-1'
	 }"
      ></div>
      <div
        class="dot"
        :style="{
		 top: '450px',
		 left: '606px',
		 zIndex: '-1'
	 }"
      ></div>
      <div
        class="dot r"
        :style="{
		 top: '751px',
		 left: '1265px',
		 zIndex: '-1'
	 }"
      ></div>
      <div
        class="dot"
        :style="{
		 top: '451px',
		 left: '-30px',
		 zIndex: '-1'
	 }"
      ></div>
    </div>
  </container>
</template>

<script>
import container from './Container'
import Title from '~/components/Title.vue'
import SocialMedia from '~/components/SocialMedia'
import Multiply from '~/components/Multiply.vue'
export default {
	components: {
		container,
		Title,
		SocialMedia,
		Multiply
	},
	props: {
		pageData: {
			type: undefined,
			required: true
		}
	},
	computed: {
		aboutMeContent() {
			return this.pageData.aboutMeContent.iv[0]
		}
	}
}
</script>

<style lang="scss">
.aboutme {
	@include largerThan(880px) {
		padding-right: 70px;
		padding-left: 40px;
	}
	.title {
		@include smallerThan(880px) {
			text-align: center;
		}
	}
	padding-right: 75px;
	@include smallerThan(880px) {
		padding-left: 75px;
	}
	margin-top: 280px;
	.row {
		@include largerThan(860px) {
			direction: rtl;
		}
		.col-6 {
			@include smallerThan(860px) {
				flex-basis: 100% !important;
				max-width: 100%;
			}
		}
	}
	.content {
		direction: ltr;
		@include smallerThan(1350px) {
			flex-basis: 60%;
			max-width: 60%;
		}
		max-width: 55%;
		padding-right: 20px;
		.data {
			@include largerThan(880px) {
				padding: 20px;
			}
			p.textContent {
				&:nth-child(2) {
					margin-top: 50px;
				}

				@include largerThan(880px) {
					margin-left: 5px;
				}
				margin-top: 30px;
				line-height: 27px;
			}
			.metaData {
				margin: 40px 0;
				ul {
					list-style: none;
					li {
						margin: 10px auto;
						font-weight: 500;
						img {
							height: 20px;
							width: 31px;
							padding: 0px auto;
						}
					}
				}
			}
			.btn {
				display: none;
				margin: 0px auto;

				@include largerThan(880px) {
					display: block;
				}
			}
		}
	}
	.imageSec {
		.groupDot {
			display: none;

			@include largerThan(880px) {
				display: block;
				top: -8px;
				position: absolute;
				z-index: 9999;
				left: -10px;
			}

			@include largerThan(1350px) {
				left: 50px !important;
			}
		}

		@include smallerThan(1350px) {
			flex-basis: 40%;
			max-width: 40%;
		}
		@include largerThan(880px) {
			margin-top: -40px;
		}
		margin-top: 40px;
		position: relative;
		padding: 20px;
		@include largerThan(1350px) {
			padding-left: 80px;
		}
		@include largerThan(1300px) {
			max-width: 45%;
		}

		@include smallerThan(860px) {
			max-width: 400px !important;
			text-align: center;
			margin: 40px auto 0 auto;
		}
		.img {
			@include largerThan(880px) {
				padding: 20px;
			}

			@include largerThan(450px) {
				padding: 7px;
			}
			height: 100%;
			img {
				@include largerThan(900px) {
					//mix-blend-mode: multiply;
				}
				filter: grayscale(100%);
				object-fit: cover;
				width: 100%;

				@include largerThan(880px) {
					height: calc(100% - 30px);
				}
				height: calc(100% - 20px);
				transition: all $transitionTime ease-in;
			}
		}
		.shadow {
			position: absolute;
			@include largerThan(1350px) {
				width: calc(100% - 317px);
			}
			@include smallerThan(1350px) {
				width: calc(100% - 257px);
			}
			@include smallerThan(900px) {
				width: 100%;
			}
			@include smallerThan(450px) {
				height: calc(100% - 20px);
			}
			background-color: $yellow;
			height: 100%;
			top: 0;
			right: 0;
			span {
				display: none;
				@include largerThan(1300px) {
					position: absolute;
					bottom: 12px;
					transform: translate(-50%);
					left: 50%;
					display: block;
				}
			}
		}
		.socialMedia {
			position: absolute;
			bottom: 3px;
			display: none;
			@include largerThan(880px) {
				display: block;
			}
			@include largerThan(1350px) {
				left: 90px;
			}
			@include smallerThan(1350px) {
				left: 30px;
			}
		}
	}
	.dot.b {
		@include smallerThan(900px) {
			top: 806px !important;
		}
	}
	.dot.a {
		@include smallerThan(900px) {
			left: 400px !important;
		}
	}
	.dot.r {
		@include smallerThan(900px) {
			top: 1140px !important;
			left: 265px !important;
		}
	}
}
</style>

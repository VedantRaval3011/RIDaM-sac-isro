<template>
  <div
    :class="containerClass"
    class="primary-data-managemet-container overflow-y-visible h-screen pt-36 flex justify-center w-screen bg-gradient-to-b from-blue-300 to-blue-200 overflow-x-hidden"
  >
    <div class="top-container">
      <div class="logo w-40">
        <img src="../../../assets/vedas.png" alt="vedas logo" />
      </div>
      <div class="leftmost-icons flex justify-around gap-3">
        <div
          class="back-button shadow-2xl rounded-full cursor-pointer mt-10 px-2 h-10 flex items-center justify-center"
          @click="$router.push('/ridam')"
        >
          <i class="fa-solid fa-circle-left text-4xl"></i>
        </div>
        <div
          class="home w-10 h-10 text-1xl rounded-full mt-10 px-2 cursor-pointer flex items-center justify-center"
          @click="$router.push('/')"
        >
          <i class="fa-solid fa-house"></i>
        </div>
        <div class="user">
          <img
            class="user-button"
            src="../../../assets/userbg.png"
            alt="user-image"
          />
        </div>
      </div>
    </div>
    <div class="mid-container">
      <div class="heading font-semibold text-lg">
        <h1 class="font-semibold mr-15 bold text-3xl">
          Primary Data Mangement
        </h1>
      </div>
      <div class="flex back">
        <button @click="$router.push('/primary-data-main-page')">
          <i class="fa-solid fa-arrow-left mt-2 text-xl ml-4"></i>
          <p class="text-back mt-2">Back</p>
        </button>
      </div>
      <form
        @submit.prevent="submitForm"
        class="form-containers flex gap-96"
        ref="container"
      >
        <div class="form-container-1" v-show="showFormContainerOne">
          <FormContainerOne
            :subtheme="subtheme"
            :theme="theme"
            :source_location="source_location"
            :name="name"
            :initialData="formData"
            @update-data="handleUpdateDataOne"
            @validate-and-proceed="ExtraFormHandleValidationAndProceed"
          />
        </div>

        <div class="extra-cont" v-show="showExtraFormContainer">
          <ExtraFormContainer
            ref="formContainerOne"
            :subtheme="subtheme"
            :theme="theme"
            :initialData="formData"
            @update-data="handleUpdateDataExtra"
            @validate-and-proceed="handleValidationAndProceed"
            @MoveBackToOne="handleMoveBackToOne"
          />
        </div>

        <div class="form-container-2">
          <FormContainerTwo
            v-show="showFormContainerTwo"
            :theme="theme"
            :subtheme="subtheme"
            :initialData="formData"
            @update-data="handleUpdateDataTwo"
            @validate-and-proceed-second-form="
              FormTwoHandleValidationAndProceed
            "
            @MoveBackToExtra="handleMoveBackToExtra"
          />
        </div>
        <div class="form-container-3">
          <FormContainerThree
            v-show="showFormContainerThree"
            :initialData="formData"
            @validate-and-proceed-form-three="
              FormThreeHandleValidationAndProceed
            "
            @update-data="handleUpdateDataThree"
            @MoveBackToTwo="handleMoveBackToTwo"
          />
        </div>
        <div class="form-container-4">
          <FormContainerFour
            v-show="showFormContainerFour"
            :initialData="formData"
            @validate-and-proceed-form-four="FormFourHandleValidationAndProceed"
            @update-data="handleUpdateDataFour"
            @MoveBackToThree="handleMoveBackToThree"
          />
        </div>
        <div class="form-container-5">
          <FormContainerFive
            v-show="showFormContainerFive"
            :initialData="formData"
            @validate-and-proceed-form-five="FormFiveHandleValidationAndProceed"
            @update-data="handleUpdateDataFive"
            @MoveBackToFour="handleMoveBackToFour"
          />
        </div>
        <div class="form-container-6">
          <FormContainerSix
            v-show="showFormContainerSix"
            :initialData="formData"
            @update-data="handleUpdateDataSix"
            @validate-and-proceed-form-six="FormSixHandleValidationAndProceed"
            @MoveBackToFive="handleMoveBackToFive"
          />
        </div>
        <div class="form-container-7">
          <FormContainerSeven
            v-show="showFormContainerSeven"
            :initialData="formData"
            @validate-and-proceed-form-seven="
              FormSevenHandleValidationAndProceed
            "
            @update-data="handleUpdateDataSeven"
            @MoveBackToSix="handleMoveBackToSix"
          />
        </div>
        <div class="form-container-8">
          <FormContainerEight
            v-show="showFormContainerEight"
            :initialData="formData"
            @validate-and-proceed-form-eight="
              FormEightHandleValidationAndProceed
            "
            @update-data="handleUpdateDataEight"
            @MoveBackToSeven="handleMoveBackToSeven"
          />
        </div>
        <div class="form-container-9">
          <FormContainerNine
            v-show="showFormContainerNine"
            :initialData="formData"
            @update-data="handleUpdateDataNine"
            @validate-and-proceed-form-nine="FormNineHandleValidationAndProceed"
            @MoveBackToEight="handleMoveBackToEight"
          />
        </div>
        <div class="form-container-10">
          <FormContainerTen
            v-show="showFormContainerTen"
            :initialData="formData"
            @update-data="handleUpdateDataTen"
            @validate-and-proceed-form-ten="FormTenHandleValidationAndProceed"
            @MoveBackToNine="handleMoveBackToNine"
          />
        </div>
        <div class="form-container-11">
          <FormContainerEleven
            v-show="showFormContainerEleven"
            :initialData="formData"
            @update-data="handleUpdateDataEleven"
            @MoveBackToTen="handleMoveBackToTen"
          />
          <div class="submit-button" v-show="showFormContainerEleven">
            <button type="submit">Submit</button>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import jsonData from "../../../../data.json";
import FormContainerOne from "../../../components/Primary-data-management/BasicDatasetInfo.vue";
import ExtraFormContainer from "../../../components/Primary-data-management/PyramindInfo.vue";
import FormContainerTwo from "../../../components/Primary-data-management/FormContainerTwo.vue";
import FormContainerThree from "../../../components/Primary-data-management/FormContainerThree.vue";
import FormContainerFour from "../../../components/Primary-data-management/FormContainerFour.vue";
import FormContainerFive from "../../../components/Primary-data-management/FormContainerFive.vue";
import FormContainerSix from "../../../components/Primary-data-management/FormContainerSix.vue";
import FormContainerSeven from "../../../components/Primary-data-management/FormContainerSeven.vue";
import FormContainerEight from "../../../components/Primary-data-management/FormContainerEight.vue";
import FormContainerNine from "../../../components/Primary-data-management/FormContainerNine.vue";
import FormContainerTen from "../../../components/Primary-data-management/FormContainerTen.vue";
import FormContainerEleven from "../../../components/Primary-data-management/FormContainerEleven.vue";

export default {
  props: ["id"],

  data() {
    return {
      showFormContainerOne: true,
      showFormContainerTwo: true,
      showExtraFormContainer: true,
      showFormContainerThree: true,
      showFormContainerFour: true,
      showFormContainerFive: true,
      showFormContainerSix: true,
      showFormContainerSeven: true,
      showFormContainerEight: true,
      showFormContainerNine: true,
      showFormContainerTen: true,
      showFormContainerEleven: true,
      screenHeight: window.innerHeight,
      jsonData: null,
      formData: null,
      selectedData: null,
      previousData: null,
      customId: "",
      theme: "",
      subtheme: "",
      source_location: "",
      projection: "",
      extension: "",
      Compression: "",
      Projection2: "",
      Projection3: "",
      CorrectProjectOne: "",
      CorrectProjectTwo: "",
      CorrectProjectThree: "",
      resampling: "",
      formCompleted: false,
    };
  },

  name: "primary-data-management",
  components: {
    FormContainerOne,
    ExtraFormContainer,
    FormContainerTwo,
    FormContainerThree,
    FormContainerFour,
    FormContainerFive,
    FormContainerSix,
    FormContainerSeven,
    FormContainerEight,
    FormContainerNine,
    FormContainerTen,
    FormContainerEleven,
  },
  computed: {
    containerClass() {
      // Return the appropriate class based on the screen height
      return {
        "h-full": this.screenHeight <= 1230,
        "h-screen": this.screenHeight > 1230,
      };
    },
  },

  mounted() {
    // Listen for window resize event and update screenHeight
    window.addEventListener("resize", this.updateScreenHeight);
    // this.fetchData();
  },

  created() {
    const id = this.$route.params.id;
    console.log("THis is id: ", id);
    console.log("this is jsonData", this.jsonData);

    if (jsonData) {
      this.jsonData = jsonData; // Assign jsonData to the component's data property
      this.filterDataById(id);
    } else {
      console.log("JSON Data is not loaded yet.");
    }
  },

  beforeDestroy() {
    // Remove the event listener to prevent memory leaks
    window.removeEventListener("resize", this.updateScreenHeight);
  },
  methods: {
    // async fetchData() {
    //   fetch('http://192.168.2.220:8001/view')
    //     .then(response => {
    //       if (!response.ok) {
    //         throw new Error('Network response was not ok');
    //       }
    //       return response.json();
    //     })
    //     .then(data => {
    //       this.previousData = data;
    //     })
    //     .catch(error => {
    //       console.error('There was a problem with the fetch operation:', error);
    //     });
    // },

    filterDataById(id) {
      console.log("ID:", id); // Log the ID being passed to the method
      console.log("json Data: ", this.jsonData);
      if (this.jsonData) {
        const filteredData = this.jsonData.find(
          (item) => item.id === id.trim()
        );
        if (filteredData) {
          this.formData = filteredData;
          console.log("Filtered Data:", this.formData);
        } else {
          console.log("No data found for ID:", id);
        }
      } else {
        console.log("JSON Data is not loaded yet.");
      }
    },

    updateScreenHeight() {
      this.screenHeight = window.innerHeight; // Update screenHeight when window is resized
    },
    // updateRowData(updatedData) {
    //   // Find the index of the row to be updated
    //   const index = this.rows.findIndex(row => row.id === updatedData.id);
    //   if (index !== -1) {
    //     // Update the row with the fetched data
    //     this.$set(this.rows, index, updatedData);
    //   } else {
    //     console.error('Row not found for update');
    //   }
    // },

    handleMoveBackToOne() {
      const formContainer = document.querySelector(".form-containers");
      const prevContainer = formContainer.querySelector(".form-container-1");
      if (formContainer && prevContainer) {
        const scrollPosition =
          prevContainer.offsetLeft - formContainer.offsetWidth;
        formContainer.scrollTo({
          left: scrollPosition,
          behavior: "smooth",
        });
      }
    },

    handleMoveBackToExtra() {
      const formContainer = document.querySelector(".form-containers");
      const prevContainer = formContainer.querySelector(".extra-cont");
      if (formContainer && prevContainer) {
        const scrollPosition = prevContainer.offsetLeft * 0.99;
        formContainer.scrollTo({
          left: scrollPosition,
          behavior: "smooth",
        });
      }
    },
    handleMoveBackToTwo() {
      const formContainer = document.querySelector(".form-containers");
      const prevContainer = formContainer.querySelector(".form-container-2");
      if (formContainer && prevContainer) {
        const scrollPosition = prevContainer.offsetLeft * 0.99;
        formContainer.scrollTo({
          left: scrollPosition,
          behavior: "smooth",
        });
      }
    },
    handleMoveBackToThree() {
      const formContainer = document.querySelector(".form-containers");
      const prevContainer = formContainer.querySelector(".form-container-3");
      if (formContainer && prevContainer) {
        const scrollPosition = prevContainer.offsetLeft;
        formContainer.scrollTo({
          left: scrollPosition,
          behavior: "smooth",
        });
      }
    },
    handleMoveBackToFour() {
      const formContainer = document.querySelector(".form-containers");
      const prevContainer = formContainer.querySelector(".form-container-4");
      if (formContainer && prevContainer) {
        const scrollPosition = prevContainer.offsetLeft * 0.99;
        formContainer.scrollTo({
          left: scrollPosition,
          behavior: "smooth",
        });
      }
    },
    handleMoveBackToFive() {
      const formContainer = document.querySelector(".form-containers");
      const prevContainer = formContainer.querySelector(".form-container-5");
      if (formContainer && prevContainer) {
        const scrollPosition = prevContainer.offsetLeft * 0.99;
        formContainer.scrollTo({
          left: scrollPosition,
          behavior: "smooth",
        });
      }
    },
    handleMoveBackToSix() {
      const formContainer = document.querySelector(".form-containers");
      const prevContainer = formContainer.querySelector(".form-container-6");
      if (formContainer && prevContainer) {
        const scrollPosition = prevContainer.offsetLeft * 0.99;
        formContainer.scrollTo({
          left: scrollPosition,
          behavior: "smooth",
        });
      }
    },
    handleMoveBackToSeven() {
      const formContainer = document.querySelector(".form-containers");
      const prevContainer = formContainer.querySelector(".form-container-7");
      if (formContainer && prevContainer) {
        const scrollPosition = prevContainer.offsetLeft * 0.99;
        formContainer.scrollTo({
          left: scrollPosition,
          behavior: "smooth",
        });
      }
    },
    handleMoveBackToEight() {
      const formContainer = document.querySelector(".form-containers");
      const prevContainer = formContainer.querySelector(".form-container-8");
      if (formContainer && prevContainer) {
        const scrollPosition = prevContainer.offsetLeft * 0.99;
        formContainer.scrollTo({
          left: scrollPosition,
          behavior: "smooth",
        });
      }
    },
    handleMoveBackToNine() {
      const formContainer = document.querySelector(".form-containers");
      const prevContainer = formContainer.querySelector(".form-container-9");
      if (formContainer && prevContainer) {
        const scrollPosition = prevContainer.offsetLeft * 0.99;
        formContainer.scrollTo({
          left: scrollPosition,
          behavior: "smooth",
        });
      }
    },
    handleMoveBackToTen() {
      const formContainer = document.querySelector(".form-containers");
      const prevContainer = formContainer.querySelector(".form-container-10");
      if (formContainer && prevContainer) {
        const scrollPosition = prevContainer.offsetLeft * 0.99;
        formContainer.scrollTo({
          left: scrollPosition,
          behavior: "smooth",
        });
      }
    },

    ExtraFormHandleValidationAndProceed() {
      const formContainer = document.querySelector(".form-containers");
      const nextContainer = formContainer.querySelector(".extra-cont");
      if (formContainer && nextContainer) {
        const nextContainerRightEdge = nextContainer.offsetLeft * 0.99;
        formContainer.scrollTo({
          left: nextContainerRightEdge,
          behavior: "smooth",
        });
      }
    },
    handleValidationAndProceed() {
      const formContainer = document.querySelector(".form-containers");
      const nextContainer = formContainer.querySelector(".form-container-2");
      if (formContainer && nextContainer) {
        const nextContainerRightEdge = nextContainer.offsetLeft * 0.99;
        formContainer.scrollTo({
          left: nextContainerRightEdge,
          behavior: "smooth",
        });
      }
    },
    FormTwoHandleValidationAndProceed() {
      const formContainer = document.querySelector(".form-containers");
      const nextContainer = formContainer.querySelector(".form-container-3");
      if (formContainer && nextContainer) {
        const nextContainerRightEdge = nextContainer.offsetLeft * 0.99;
        formContainer.scrollTo({
          left: nextContainerRightEdge,
          behavior: "smooth",
        });
      }
    },
    FormThreeHandleValidationAndProceed() {
      const formContainer = document.querySelector(".form-containers");
      const nextContainer = formContainer.querySelector(".form-container-4");
      if (formContainer && nextContainer) {
        const nextContainerRightEdge = nextContainer.offsetLeft * 0.99;
        formContainer.scrollTo({
          left: nextContainerRightEdge,
          behavior: "smooth",
        });
      }
    },
    FormFourHandleValidationAndProceed() {
      const formContainer = document.querySelector(".form-containers");
      const nextContainer = formContainer.querySelector(".form-container-5");
      if (formContainer && nextContainer) {
        const nextContainerRightEdge = nextContainer.offsetLeft * 0.99;
        formContainer.scrollTo({
          left: nextContainerRightEdge,
          behavior: "smooth",
        });
      }
    },
    FormFiveHandleValidationAndProceed() {
      const formContainer = document.querySelector(".form-containers");
      const nextContainer = formContainer.querySelector(".form-container-6");
      if (formContainer && nextContainer) {
        const nextContainerRightEdge = nextContainer.offsetLeft * 0.99;
        formContainer.scrollTo({
          left: nextContainerRightEdge,
          behavior: "smooth",
        });
      }
    },
    FormSixHandleValidationAndProceed() {
      const formContainer = document.querySelector(".form-containers");
      const nextContainer = formContainer.querySelector(".form-container-7");
      if (formContainer && nextContainer) {
        const nextContainerRightEdge = nextContainer.offsetLeft * 0.99;
        formContainer.scrollTo({
          left: nextContainerRightEdge,
          behavior: "smooth",
        });
      }
    },
    FormSevenHandleValidationAndProceed() {
      const formContainer = document.querySelector(".form-containers");
      const nextContainer = formContainer.querySelector(".form-container-8");
      if (formContainer && nextContainer) {
        const nextContainerRightEdge = nextContainer.offsetLeft * 0.99;
        formContainer.scrollTo({
          left: nextContainerRightEdge,
          behavior: "smooth",
        });
      }
    },
    FormEightHandleValidationAndProceed() {
      const formContainer = document.querySelector(".form-containers");
      const nextContainer = formContainer.querySelector(".form-container-9");
      if (formContainer && nextContainer) {
        const nextContainerRightEdge = nextContainer.offsetLeft * 0.99;
        formContainer.scrollTo({
          left: nextContainerRightEdge,
          behavior: "smooth",
        });
      }
    },
    FormNineHandleValidationAndProceed() {
      const formContainer = document.querySelector(".form-containers");
      const nextContainer = formContainer.querySelector(".form-container-10");
      if (formContainer && nextContainer) {
        const nextContainerRightEdge = nextContainer.offsetLeft * 0.99;
        formContainer.scrollTo({
          left: nextContainerRightEdge,
          behavior: "smooth",
        });
      }
    },
    FormTenHandleValidationAndProceed() {
      const formContainer = document.querySelector(".form-containers");
      const nextContainer = formContainer.querySelector(".form-container-11");
      if (formContainer && nextContainer) {
        const nextContainerRightEdge = nextContainer.offsetLeft * 0.99;
        formContainer.scrollTo({
          left: nextContainerRightEdge,
          behavior: "smooth",
        });
      }
    },
    handleUpdateDataOne(data) {
      this.subtheme = data.subtheme;
      this.theme = data.theme;
      this.source_location = data.sourcelocation;
      this.productId = data.productId;
      this.name = data.name;
      this.source_locations = data.sourcelocations;
    },
    handleUpdateDataExtra(data) {
      // Update your data properties with the emitted data from the child component

      this.extension = data.extension;
      this.Compression = data.Compression;
      this.projection = data.projection;
      this.Projection2 = data.Projection2;
      this.Projection3 = data.Projection3;
      this.CorrectProjectOne = data.CorrectProjectOne;
      this.CorrectProjectTwo = data.CorrectProjectTwo;
      this.CorrectProjectThree = data.CorrectProjectThree;
      this.resampling = data.resampling;
      this.interleave = data.interleave;
      this.temporal_frequency = data.temporal_frequency;
      this.paused = data.paused;
    },
    handleUpdateDataTwo(data) {
      // Update your data properties with the emitted data from the child component

      this.status = data.status;
      this.edition = data.edition;
      this.dataType = data.dataType;
      this.AccessConstraint = data.AccessConstraint;
      this.CorrectAccessConstraints = data.CorrectAccessConstraints;
      this.UseConstraints = data.UseConstraints;
      this.CorrectUseConstraints = data.CorrectUseConstraints;
      this.Purpose = data.Purpose;
      this.CorrectPurpose = data.CorrectPurpose;
      this.firstRowKeywords = data.firstRowKeywords;
      this.secondRowKeywords = data.secondRowKeywords;
    },
    handleUpdateDataThree(data) {
      // Update your data properties with the emitted data from the child component
      this.city = data.city;
      this.country = data.country;
      this.ContactPerson = data.ContactPerson;
      this.CorrectContactPerson = data.CorrectContactPerson;
      this.ContactTelephone = data.ContactTelephone;
      this.CorrectContactTelephone = data.CorrectContactTelephone;
      this.organization = data.organization;
      this.CorrectOrganization = data.CorrectOrganization;
      this.MailAddress = data.MailAddress;
      this.CorrectMailAddress = data.CorrectMailAddress;
      this.CorrectFaxNumber = data.CorrectFaxNumber;
      this.FaxNumber = data.FaxNumber;
    },
    handleUpdateDataFour(data) {
      // Update your data properties with the emitted data from the child component

      this.datum = data.datum;
      this.spheroid = data.spheroid;
      this.CorrectSpheroid = data.CorrectSpheroid;
      this.CorrectDatum = data.CorrectDatum;
    },
    handleUpdateDataFive(data) {
      // Update your data properties with the emitted data from the child component

      this.yLl = data.yLl;
      this.CorrectYLl = data.CorrectYLl;
      this.xLl = data.xLl;
      this.CorrectXLl = data.CorrectXLl;
      this.yLr = data.yLr;
      this.CorrectYlr = data.CorrectYlr;
      this.xLr = data.xLr;
      this.CorrectXlr = data.CorrectXlr;
      this.xUl = data.xUl;
      this.CorrectXUl = data.CorrectXUl;
      this.yUl = data.yUl;
      this.CorrectYUl = data.CorrectYUl;
      this.xUr = data.xUr;
      this.CorrectXUr = data.CorrectXUr;
      this.yUr = data.yUr;
      this.CorrectYUr = data.CorrectYUr;
    },

    handleUpdateDataSix(data) {
      // Update your data properties with the emitted data from the child component
      this.date = data.date;
    },

    handleUpdateDataSeven(data) {
      this.dpb = data.dpb;
      this.Correctdpb = data.Correctdpb;
      this.ogsc = data.ogsc;
      this.CorrectOgsc = data.CorrectOgsc;
      this.CorrectSourceScale = data.CorrectSourceScale;
      this.SourceScale = data.SourceScale;
      this.SourceDate = data.SourceDate;
      this.Lineage = data.Lineage;
      this.CorrectLineage = data.CorrectLineage;
      this.cn = data.cn;
      this.CorrectCn = data.CorrectCn;
      this.ad = data.ad;
      this.CorrectAd = data.CorrectAd;
    },

    handleUpdateDataEight(data) {
      // Update your data properties with the emitted data from the child component
      this.DITC = data.DITC;
    },
    handleUpdateDataNine(data) {
      // Update your data properties with the emitted data from the child component
      this.language = data.language;
      this.Correctlanguage = data.Correctlanguage;
    },
    handleUpdateDataTen(data) {
      // Update your data properties with the emitted data from the child component
      this.dia = data.dia;
      this.CorrectDia = data.CorrectDia;
    },
    handleUpdateDataEleven(data) {
      // Update your data properties with the emitted data from the child component
      this.pd = data.pd;
      this.Correctpd = data.Correctpd;
      this.accReport = data.accReport;
      this.CorrectAccR = data.CorrectAccR;
      this.horpor = data.horpor;
      this.Correcthorpor = data.Correcthorpor;
    },

    checkScreenHeight() {
      const screenHeight = window.innerHeight; // Height of the screen
      const pdmContainer = document.querySelector(
        ".primary-data-managemet-container"
      ); // Select the .primary-data-managemet-container element

      if (screenHeight >= 1230) {
        pdmContainer.classList.add("w-screen"); // Add the w-screen class if the height is 1230 or more
      } else {
        pdmContainer.classList.remove("w-screen"); // Remove the w-screen class if the height is less than 1230
      }
    },

    submitForm() {
      // Check if all data properties are populated
      if (
        this.name &&
        this.productId &&
        this.pd &&
        this.Correctpd &&
        this.accReport &&
        this.CorrectAccR &&
        this.horpor &&
        this.Correcthorpor &&
        this.DITC &&
        this.dpb &&
        this.Correctdpb &&
        this.ogsc &&
        this.CorrectSourceScale &&
        this.SourceScale &&
        this.SourceDate &&
        this.Lineage &&
        this.CorrectLineage &&
        this.cn &&
        this.CorrectCn &&
        this.ad &&
        this.CorrectAd &&
        this.date &&
        this.yLl &&
        this.CorrectYLl &&
        this.xLl &&
        this.CorrectXLl &&
        this.yLr &&
        this.CorrectYlr &&
        this.xLr &&
        this.CorrectXlr &&
        this.xUl &&
        this.CorrectXUl &&
        this.yUl &&
        this.CorrectYUl &&
        this.xUr &&
        this.CorrectXUr &&
        this.yUr &&
        this.CorrectYUr &&
        this.source_location &&
        this.subtheme &&
        this.projection &&
        this.extension &&
        this.resampling &&
        this.Compression &&
        this.Projection2 &&
        this.Projection3 &&
        this.CorrectProjectOne &&
        this.CorrectProjectTwo &&
        this.CorrectProjectThree &&
        this.city &&
        this.country &&
        this.ContactPerson &&
        this.CorrectContactPerson &&
        this.ContactTelephone &&
        this.CorrectContactTelephone &&
        this.organization &&
        this.CorrectOrganization &&
        this.MailAddress &&
        this.CorrectMailAddress &&
        this.FaxNumber &&
        this.status &&
        this.edition &&
        this.dataType &&
        this.AccessConstraint &&
        this.CorrectAccessConstraints &&
        this.UseConstraints &&
        this.CorrectUseConstraints &&
        this.Purpose &&
        this.CorrectPurpose &&
        this.firstRowKeywords &&
        this.secondRowKeywords &&
        this.datum &&
        this.spheroid &&
        this.CorrectSpheroid &&
        this.CorrectDatum &&
        this.projection &&
        this.extension
      ) {
        // const dataToUpdate = {
        //   name: this.name,
        //   source_location: this.source_location,

        //   metadata: {
        //     access_constraints: this.AccessConstraint,
        //     use_constraints: this.UseConstraints,
        //     purpose: this.Purpose,
        //     contact_person: this.ContactPerson,
        //     organization: this.Organization,
        //     mailng_address: this.MailAddress,
        //     city: this.city,
        //     country: this.country,
        //     contact_telephone: this.ContactTelephone,
        //     contact_fax: this.FaxNumber,
        //     contact_email: this.MailAddress,
        //     spheroid: this.Spheroid,
        //     datum: this.Datum,
        //     x_ul: this.xUl,
        //     y_ul: this.yUl,
        //     x_ur: this.xUr,
        //     y_ur: this.yUr,
        //     x_ll: this.xLl,
        //     y_ll: this.yLl,
        //     x_lr: this.xLr,
        //     y_lr: this.yLr,
        //     metadata_stamp_date: this.date,
        //     dpb: this.dpb,
        //     osgc: this.ogsc,
        //     source_scale: this.SourceScale,
        //     source_date: this.SourceDate,
        //     lineage: this.Lineage,
        //     corporate_name: this.cn,
        //     corporate_address: this.ad,
        //     ditc: this.DITC,
        //     language: this.language,
        //     dia: this.dia,
        //     pd: this.pd,
        //     accReport: this.accReport,
        //     horpor: this.horpor,
        //     subtheme: this.subtheme,
        //     organization: this.organization,
        //     theme: this.theme,
        //   },
        // };

        console.log(this.source_location);
        // Update the corresponding entry in jsonData
        const id = this.$route.params.id;

        const index = jsonData.findIndex((item) => item.id === id.trim());

        if (index !== -1) {
          const dataToUpdate = jsonData[index]; // Get the existing data object

          // Update the properties of the retrieved data object using values from 'this'
          dataToUpdate.name = this.name;
          dataToUpdate.source_location = this.source_location;
          dataToUpdate.metadata.access_constraints = this.AccessConstraint;
          dataToUpdate.metadata.use_constraints = this.UseConstraints;
          dataToUpdate.metadata.purpose = this.Purpose;
          dataToUpdate.metadata.contact_person = this.ContactPerson;
          dataToUpdate.metadata.organization = this.Organization;
          dataToUpdate.metadata.mailng_address = this.MailAddress;
          dataToUpdate.metadata.city = this.city;
          dataToUpdate.metadata.country = this.country;
          dataToUpdate.metadata.contact_telephone = this.ContactTelephone;
          dataToUpdate.metadata.contact_fax = this.FaxNumber;
          dataToUpdate.metadata.contact_email = this.MailAddress;
          dataToUpdate.metadata.spheroid = this.Spheroid;
          dataToUpdate.metadata.datum = this.Datum;
          dataToUpdate.metadata.x_ul = this.xUl;
          dataToUpdate.metadata.y_ul = this.yUl;
          dataToUpdate.metadata.x_ur = this.xUr;
          dataToUpdate.metadata.y_ur = this.yUr;
          dataToUpdate.metadata.x_ll = this.xLl;
          dataToUpdate.metadata.y_ll = this.yLl;
          dataToUpdate.metadata.x_lr = this.xLr;
          dataToUpdate.metadata.y_lr = this.yLr;
          dataToUpdate.metadata.metadata_stamp_date = this.date;
          dataToUpdate.metadata.dpb = this.dpb;
          dataToUpdate.metadata.osgc = this.ogsc;
          dataToUpdate.metadata.source_scale = this.SourceScale;
          dataToUpdate.metadata.source_date = this.SourceDate;
          dataToUpdate.metadata.lineage = this.Lineage;
          dataToUpdate.metadata.corporate_name = this.cn;
          dataToUpdate.metadata.corporate_address = this.ad;
          dataToUpdate.metadata.ditc = this.DITC;
          dataToUpdate.metadata.language = this.language;
          dataToUpdate.metadata.dia = this.dia;
          dataToUpdate.metadata.pd = this.pd;
          dataToUpdate.metadata.accReport = this.accReport;
          dataToUpdate.metadata.horpor = this.horpor;
          dataToUpdate.metadata.subtheme = this.subtheme;
          dataToUpdate.metadata.organization = this.organization;
          dataToUpdate.metadata.theme = this.theme; // Update the data in jsonData array
          console.log("Updated Data:", dataToUpdate);
          alert("Data updated successfully!");
        } else {
          console.log("No data found for ID:", id);
        }

        // console.log("Id Test-=------");
        // console.log(this.id);
        // // All data is entered, proceed with form submission
        // fetch("http://192.168.2.220:8001/update/" + this.id, {
        //   method: "POST",
        //   headers: {
        //     "Content-Type": "application/json",
        //   },
        //   body: JSON.stringify(dataToUpdate),
        // })
        //   .then((response) => {
        //     if (response.ok) {

        //       return response.json();
        //     } else {
        //       throw new Error("Failed to submit data");
        //     }
        //   })
        //   .then((responseData) => {
        //     console.log("Response Data:", responseData);
        //     alert("Data submitted successfully!");
        //   })
        //   .catch((error) => {
        //     console.log(this.body);
        //     console.error(error);
        //     alert("Failed to submit data. Please try again.");
        //   });
      } else {
        // Data is incomplete, show error message to the user

        alert("Please fill in all the required fields.");
        //error
      }
    },
  },
};
</script>
<style scoped>
body,
html {
  margin: 0;
  padding: 0;
  height: 100%;
  scroll-behavior: smooth;
}

button {
  --clr-font-main: hsla(0 0% 20% / 100);
  --btn-bg-1: hsla(194 100% 69% / 1);
  --btn-bg-2: hsla(217 100% 56% / 1);
  --btn-bg-color: hsla(360 100% 100% / 1);
  --radii: 0.5em;
  cursor: pointer;

  font-size: var(--size, 1rem);
  font-family: "Segoe UI", system-ui, sans-serif;
  font-weight: 500;
  transition: 0.8s;
  background-size: 280% auto;
  background-image: linear-gradient(
    325deg,
    var(--btn-bg-2) 0%,
    var(--btn-bg-1) 55%,
    var(--btn-bg-2) 90%
  );
  border: none;
  width: 4rem;
  height: 2.5rem;
  border-radius: var(--radii);
  color: var(--btn-bg-color);
  box-shadow: 0px 0px 20px rgba(71, 184, 255, 0.5),
    0px 5px 5px -1px rgba(58, 125, 233, 0.25),
    inset 4px 4px 8px rgba(175, 230, 255, 0.5),
    inset -4px -4px 8px rgba(19, 95, 216, 0.35);
}

button:hover {
  background-position: right top;
}

button:is(:focus, :focus-visible, :active) {
  outline: none;
  box-shadow: 0 0 0 3px var(--btn-bg-color), 0 0 0 6px var(--btn-bg-2);
}

@media (prefers-reduced-motion: reduce) {
  button {
    transition: linear;
  }
}

.submit-button button {
  display: flex;
  justify-content: center;
  align-items: center;
}

.submit-button {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  bottom: 6rem;
}

.top-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  padding: 0;
  display: flex;
  justify-content: space-between;
}

.back-button {
  color: #2756ff;
}

.logo {
  margin-right: 2em; /* Add some spacing between the logo and other content */
}

.home {
  background-color: #2756ff;
  color: #97c7fd;
}

.logo img {
  margin-left: 1em;
}

.user-button {
  width: 2rem;
  margin-top: 1rem;
  margin-right: 2rem;
  border-radius: 50%; /* Add rounded corners */
  box-shadow: 0px 1px 5px rgb(94, 77, 77);
}

.form-container-6 {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.user-button:hover {
  box-shadow: 0px 0px 0px rgb(94, 77, 77);
  cursor: pointer;
  z-index: 20;
}

.user-button {
  --clr-font-main: hsla(0 0% 20% / 100);
  --btn-bg-1: rgb(65, 145, 249);
  --btn-bg-2: hsla(194 100% 56% / 1);
  --btn-bg-color: hsla(360 100% 100% / 1);
  --radii: 0.5em;
  cursor: pointer;

  font-size: var(--size, 1rem);
  font-family: "Segoe UI", system-ui, sans-serif;
  font-weight: 500;
  transition: 0.8s;
  background-size: 280% auto;
  border: none;
  width: 5rem;
  border-radius: 50%;
  color: var(--btn-bg-color);
  box-shadow: 0px 0px 20px rgba(71, 184, 255, 0.5),
    0px 5px 5px -1px rgba(58, 125, 233, 0.25),
    inset 4px 4px 8px rgba(175, 230, 255, 0.5),
    inset -4px -4px 8px rgba(19, 95, 216, 0.35);
}

.user-button:hover {
  background-position: right top;
}

.user-button:is(:focus, :focus-visible, :active) {
  outline: none;
  box-shadow: 0 0 0 3px var(--btn-bg-color), 0 0 0 6px var(--btn-bg-2);
}

@media (prefers-reduced-motion: reduce) {
  .user-button {
    transition: linear;
  }
}

.text-back {
  margin-right: 12%;
  font-size: 16px;
}

button {
  display: flex;
  justify-content: space-between;
  width: 6rem;
  border-radius: 50px; /* Add rounded corners */
  box-shadow: 0px 1px 5px rgb(94, 77, 77);
  margin-bottom: 1rem;
  margin-top: 1rem;
  position: relative;
}

.form-containers {
  display: flex;
  position: relative;
  justify-content: flex-start;
  align-items: center;
  transition: transform 0.5s ease;
  gap: 17.85rem;
  overflow-x: hidden;
  overflow-y: hidden;
  max-width: 100%;
  width: 35rem;
  white-space: nowrap;
  padding-left: 8%;
  scroll-behavior: smooth; /* Apply smooth scroll behavior */
  scroll-snap-type: x mandatory; /* Ensure smooth snapping behavior */
  scroll-padding: 0 1rem;
}

::-webkit-scrollbar {
  display: none;
}

.form-container-1,
.form-container-2,
.form-container-3,
.form-container-6,
.form-container-4,
.form-container-5,
.form-container-6,
.form-container-7,
.form-container-8,
.form-container-9,
.form-container-10,
.form-container-11 {
  z-index: 999;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}

/* Base styles */

@media screen and (max-width: 640px) {
  /* Small mobile devices */
  .logo img {
    width: 50%;
    margin-top: 1rem;
  }
  .user-button {
    width: 3rem;
    margin: 0;
    margin-right: 1rem;
    margin-top: 1rem;
  }
  h1 {
    font-size: 100%;
    margin-right: 5%;
  }

  .back {
    margin-left: 25%;
  }
  .form-containers {
    align-items: baseline;
  }

  .submit-button {
    right: 6rem;
  }
}

@media screen and (min-width: 641px) and (max-width: 767px) {
  /* Big mobile devices */
}

@media screen and (min-width: 768px) and (max-width: 1023px) {
  /* Small laptops and tablets */
}

@media screen and (min-width: 1024px) and (max-width: 1279px) {
  /* Big laptops and desktops */
}
@media screen and (min-width: 1280px) and (max-width: 1440px) {
  /* Big laptops and desktops */
}
@media screen and (min-width: 1441px) {
  /* Big laptops and desktops */
}
</style>

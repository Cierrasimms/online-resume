<template>
  <div class="home">
    <h2>{{ user.first_name }} {{ user.last_name }}</h2>
  </div>
  <div class="col d-flex justify-content-center">
    <div class="card col-md-3 mx-3" style="max-width: 18rem">
      <img
        src="https://i1.sndcdn.com/artworks-000250680664-2frnod-t500x500.jpg"
        class="circular--square"
        alt="student.first_name"
      />
      <div class="card-body">
        <h5 class="card-title">{{ student.first_name }} {{ student.last_name }}</h5>
        <p class="card-text">He is {{ student.first_name }}</p>
      </div>
      <div class="card-body">
        <a href="#" class="card-link">{{ student.email }}</a>
        <br />
        <a href="#" class="card-link">{{ student.phone_number }}</a>
      </div>
    </div>
  </div>
  <div class="col d-flex justify-content-center">
    <div class="card col-md-3 mx-3" style="max-width: 18rem">
      <div class="card-header">About Me</div>
      <div class="card-body">
        <blockquote class="blockquote mb-0">
          <h2>I am {{ student.first_name }}</h2>
        </blockquote>
        <p>{{ student.short_bio }}</p>
        <h5>LinkedIn: {{ student.linkedin_url }}</h5>
        <h5>GitHub: {{ student.github_url }}</h5>
      </div>
    </div>
  </div>
  <div>
    <section id="resume" class="resume">
      <div class="container" data-aos="fade-up">
        <div class="section-title">
          <h2>Resume</h2>
        </div>

        <div class="row">
          <div class="col-lg-6">
            <h3 class="resume-title"></h3>

            <h3 class="resume-education">Education</h3>
            <div v-for="education in educations" v-bind:key="education.id">
              <div class="resume-item">
                <h4>{{ education.degree }}</h4>
                <h5>{{ education.start_date }} - {{ education.end_date }}</h5>
                <p>
                  <em>{{ education.university_name }}</em>
                </p>
              </div>
            </div>

            <!-- <div class="resume-item">
              <h4>Degree title</h4>
              <h5>2015 - 2016</h5>
              <p><em>location</em></p>
            </div> -->
          </div>
          <div class="col-lg-6">
            <div>
              <h3 class="resume-experience">Professional Experience</h3>
              <div v-for="experience in experiences" v-bind:key="experience.id" class="resume-item">
                <h4>{{ experience.job_title }}</h4>
                <h5>2019 - Present</h5>

                <li>{{ experience.details }}</li>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
  <div>
    <a
      class="twitter-timeline"
      data-width="500"
      data-height="900"
      v-bind:href="`https://twitter.com/` + student.twitter_handle"
    >
      Tweets by {{ student.twitter_handle }}
    </a>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      currentUser: {},
      user: {},
      student: {},
      educations: [],
      experiences: [],
    };
  },
  mounted() {
    let externalScript = document.createElement("script");
    externalScript.setAttribute("src", "https://platform.twitter.com/widgets.js");

    document.head.appendChild(externalScript);
  },
  created: function () {
    this.resumeShow();
    this.studentShow();
    this.educationShow();
    this.experienceShow();
  },
  methods: {
    resumeShow: function () {
      axios.get("https://swapi.dev/api/people/1/").then((response) => {
        // console.log(response.data);
        this.user = response.data;
      });
    },
    studentShow: function () {
      axios.get("/students/1").then((response) => {
        console.log(response.data);
        this.student = response.data;
      });
    },
    educationShow: function () {
      axios.get("/educations").then((response) => {
        console.log(response.data);
        this.educations = response.data;
      });
    },
    experienceShow: function () {
      axios.get("/experiences").then((response) => {
        // There is currently no data for experiences, so it currently returns nothing
        console.log(response.data);
        this.experiences = response.data;
      });
    },
  },
};
</script>

<style>
.resume .resume-title {
  text-decoration: underline;
  font-size: 26px;
  font-weight: 700;
  margin-top: 20px;
  margin-bottom: 20px;
  color: #000000;
}
.resume .resume-item {
  padding: 0 0 20px 20px;
  margin-top: -2px;
  border-left: 2px solid #000000;
  position: relative;
}
.resume .resume-item h4 {
  line-height: 18px;
  font-size: 18px;
  font-weight: 600;
  text-transform: uppercase;
  font-family: "Poppins", sans-serif;
  color: #000000;
  margin-bottom: 10px;
}
.resume .resume-item h5 {
  font-size: 16px;
  background: #f7f8f9;
  padding: 5px 15px;
  display: inline-block;
  font-weight: 600;
  margin-bottom: 10px;
}
.resume .resume-item ul {
  padding-left: 20px;
}
.resume .resume-item ul li {
  padding-bottom: 10px;
}
.resume .resume-item:last-child {
  padding-bottom: 0;
}
.resume .resume-item::before {
  content: "";
  position: absolute;
  width: 16px;
  height: 16px;
  border-radius: 50px;
  left: -9px;
  top: 0;
  background: #fff;
  border: 2px solid #000000;
}
.circular--square {
  border-radius: 50%;
  display: block;
  margin-left: auto;
  margin-right: auto;

  padding: 5px;
}
.resume .resume-education {
  color: black;
  text-decoration: underline;
}
.resume .resume-experience {
  color: black;
  text-decoration: underline;
}
img {
  max-width: 70%;
  height: auto;
  border-radius: 70%;
}
.resume .section-title {
  text-decoration: underline;
}
.resume .resume-title {
  font-size: 26px;
  text-decoration: underline;
  font-weight: 700;
  margin-top: 20px;
  margin-bottom: 20px;
  color: #45505b;
}
.resume .resume-item {
  padding: 0 0 20px 20px;
  margin-top: -2px;
  border-left: 2px solid #0563bb;
  position: relative;
}
.resume .resume-item h4 {
  line-height: 18px;
  font-size: 18px;
  font-weight: 600;
  text-transform: uppercase;
  font-family: "Poppins", sans-serif;
  color: #0563bb;
  margin-bottom: 10px;
}
.resume .resume-item h5 {
  font-size: 16px;
  background: #f7f8f9;
  padding: 5px 15px;
  display: inline-block;
  font-weight: 600;
  margin-bottom: 10px;
}
.resume .resume-item ul {
  padding-left: 20px;
}
.resume .resume-item ul li {
  padding-bottom: 10px;
}
.resume .resume-item:last-child {
  padding-bottom: 0;
}
.resume .resume-item::before {
  content: "";
  position: absolute;
  width: 16px;
  height: 16px;
  border-radius: 50px;
  left: -9px;
  top: 0;
  background: #fff;
  background-color: grey;
  border: 2px solid #0563bb;
}
body {
  background-image: url("https://coolbackgrounds.io/images/backgrounds/index/sea-edge-79ab30e2.png");
  background-size: cover;
  background-repeat: no-repeat;
}
.card {
  margin-bottom: 15px;
  /* background-color: rgb(205, 231, 238); */
  background-image: url("https://coolbackgrounds.io/images/backgrounds/index/ranger-4df6c1b6.png");
  font-family: "Roboto", sans-serif;
}
h5 {
  font-weight: bolder;
  color: black;
}
h4 {
  color: black;
}
</style>

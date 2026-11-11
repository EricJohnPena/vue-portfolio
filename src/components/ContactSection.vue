<script setup>
import { Notyf } from 'notyf';
import { ref, onMounted, onBeforeUnmount } from 'vue';
import axios from "axios";
import 'notyf/notyf.min.css';

const notyf = new Notyf();

const WEB3FORMS_ACCESS_KEY="dea57d55-0cd0-4f51-b8e4-9273597e1588";

//initial value for the email
const subject = "New message from Portfolio Contact Form";
const SITE_KEY = "6LfdqRouAAAAAD35NLSsre_XZPOJ8hu99HqE2lWq";
const name = ref("");
const email = ref("");
const message = ref("");
const isLoading = ref(false);

//function for sending the email
const submitForm = async() => {
    isLoading.value = true;

    if (!recaptchaToken.value) {
        notyf.error('Please verify that you are not a robot.');
        return;
    }

    try {
        const response = await axios.post('https://api.web3forms.com/submit', 
            {
                access_key : WEB3FORMS_ACCESS_KEY,
                subject: subject,
                name: name.value,
                email: email.value,
                message: message.value
            }, {
                headers: {
                    'Content-Type' : "application/json",
                    Accept: "application/json"
                }
            }
        )
        
        const result = response.data;

        if (result.success){
            notyf.success("Message Sent!");
            
            name.value = "";
            email.value = "";
            message.value = "";
        }

    } catch (error) {
        notyf.error("Failed to send email")
    }finally{
        isLoading.value = false;
    }
}


const recaptchaContainer = ref(null);
const recaptchaWidgetId = ref(null);
const recaptchaToken = ref('');

// Callback called by reCAPTCHA when successful
function onRecaptchaSuccess(token) {
  recaptchaToken.value = token;
}

// Callback when expired
function onRecaptchaExpired() {
  recaptchaToken.value = '';
}

// Function to render the reCAPTCHA widget
function renderRecaptcha() {
  if (!window.grecaptcha) {
    console.error('reCAPTCHA not loaded');
    return;
  }

  recaptchaWidgetId.value = window.grecaptcha.render(recaptchaContainer.value, {
    sitekey: SITE_KEY,
    size: 'normal', // or 'compact'
    callback: onRecaptchaSuccess,
    'expired-callback': onRecaptchaExpired,
  });
}

// Function to reset reCAPTCHA 
function resetRecaptcha() {
  if (recaptchaWidgetId.value !== null) {
    window.grecaptcha.reset(recaptchaWidgetId.value);
    recaptchaToken.value = '';
  }
}



onMounted(() => {
  // This code waits for the Google reCAPTCHA library to load, then renders the reCAPTCHA widget using onMounted hook. 
  // The widget is rendered with grecaptcha.render(), which requires a sitekey. 
  // Callback functions handle success and expiration events. 
  // reCAPTCHA is reset upon form submission to clear the token.
  const interval = setInterval(() => {
    if (window.grecaptcha && window.grecaptcha.render) {
      renderRecaptcha();
      clearInterval(interval);
    }
  }, 100);

  onBeforeUnmount(() => {
    clearInterval(interval);
  });
});

</script>
<template>
    <!-- Contact Section Start-->
    <section id="contact" class="container-fluid p-0 border-top">
        <div class="row m-0">
            <!-- Left Side: Form -->
            <div class="col-lg-6 p-5 d-flex justify-content-center">
                <div class="contact-form-wrapper w-100" >
                    <h3 class="fw-bold mb-2">Send a Message</h3>
                    <p class="text-muted small mb-4">Have an idea or project? Let's talk about building something great.</p>
                    <form @submit.prevent="submitForm">
                        <div class="mb-3">
                            <label class="form-label small fw-bold text-muted">YOUR NAME</label>
                            <input v-model="name" type="text" class="form-control bg-light border-0 py-2" placeholder="Jane Doe">
                        </div>
                        <div class="mb-3">
                            <label class="form-label small fw-bold text-muted">EMAIL ADDRESS</label>
                            <input v-model="email" type="email" class="form-control bg-light border-0 py-2" placeholder="jane@example.com">
                        </div>
                        <div class="mb-4">
                            <label class="form-label small fw-bold text-muted">PROJECT DETAILS</label>
                            <textarea v-model="message" class="form-control bg-light border-0 py-2" rows="4" placeholder="Tell me about your goals, timelines, and scope..."></textarea>
                        </div>
                        <button type="submit" class="btn btn-dark-custom px-4 py-2">SEND MESSAGE</button>

                         <!-- recaptcha checkbox -->
                    <div class="d-flex justify-content-end mt-2">
                        <div ref="recaptchaContainer"></div>
                    </div>
                    </form>
                </div>
            </div>
            
            <!-- Right Side: Info -->
            <div class="col-lg-6 p-5 d-flex justify-content-center bg-contact-info">
                <div class="contact-info-wrapper w-100">
                    <span class="section-badge mb-3 d-inline-block">CONTACT</span>
                    <h3 class="fw-bold mb-2">Get in Touch</h3>
                    <p class="text-muted small mb-4">Available for freelance contracts, design leadership, and full-time inquiries.</p>
                    
                    <div class="row g-3">
                        <div class="col-md-6">
                            <div class="contact-info-card">
                                <div class="contact-icon"><i aria-hidden="true" class="fas fa-envelope"></i></div>
                                <div>
                                    <div class="info-label">EMAIL</div>
                                    <div id="info-mail" class="info-value">eric.john.pena@gmail.com</div>
                                </div>
                            </div>
                        </div>
                        <div class="col-md-6">
                            <div class="contact-info-card">
                                <div class="contact-icon"><i aria-hidden="true" class="fas fa-map-marker-alt"></i></div>
                                <div>
                                    <div class="info-label">LOCATION</div>
                                    <div class="info-value">Cavite, Philippines</div>
                                </div>
                            </div>
                        </div>
                        <div class="col-md-6">
                            <div class="contact-info-card">
                                <div class="contact-icon"><a href="https://github.com/EricJohnPena" target="_blank"><i aria-hidden="true" class="fab fa-github"></i></a></div>
                                <div>
                                    <div class="info-label">GITHUB</div>
                                    <div class="info-value">github.com/EricJohnPena</div>
                                </div>
                            </div>
                        </div>
                        <div class="col-md-6">
                            <div class="contact-info-card">
                                <div class="contact-icon"><a href="https://www.linkedin.com/in/eric-john-peña-352925284" target="_blank"><i aria-hidden="true" class="fab fa-linkedin-in"></i></a></div>
                                <div>
                                    <div class="info-label">NETWORK</div>
                                    <div class="info-value">linkedin.com</div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Scontact Section End -->
</template>
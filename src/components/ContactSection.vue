<template>
    <!-- Contact Section Start-->
    <section id="contact" class="container-fluid p-0 border-top">
        <div class="row m-0">
            <!-- Left Side: Form -->
            <div class="col-lg-6 p-5 d-flex justify-content-center">
                <div class="contact-form-wrapper w-100" >
                    <h3 class="fw-bold mb-2">Send a Message</h3>
                    <p class="text-muted small mb-4">Have an idea or project? Let's talk about building something great.</p>
                    <form>
                        <div class="mb-3">
                            <label class="form-label small fw-bold text-muted">YOUR NAME</label>
                            <input type="text" class="form-control bg-light border-0 py-2" placeholder="Jane Doe">
                        </div>
                        <div class="mb-3">
                            <label class="form-label small fw-bold text-muted">EMAIL ADDRESS</label>
                            <input type="email" class="form-control bg-light border-0 py-2" placeholder="jane@example.com">
                        </div>
                        <div class="mb-4">
                            <label class="form-label small fw-bold text-muted">PROJECT DETAILS</label>
                            <textarea class="form-control bg-light border-0 py-2" rows="4" placeholder="Tell me about your goals, timelines, and scope..."></textarea>
                        </div>
                        <button type="submit" class="btn btn-dark-custom px-4 py-2">SEND MESSAGE</button>
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
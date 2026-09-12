<script setup>
import { ref, nextTick } from 'vue'
import { ArrowUpRight, ArrowRight, Menu, X, Globe2, Plane, Warehouse, Leaf, ChevronDown, Check, Mail, Phone, Linkedin, Instagram } from 'lucide-vue-next'

const menuOpen = ref(false)
const quoteOpen = ref(false)
const activeService = ref(0)
const submitted = ref(false)
const services = [
  { title: 'Air Freight', text: 'Time-critical cargo, moved with precision across every continent.', icon: Plane, tag: '01', image: 'https://images.unsplash.com/photo-1436491865332-7a61a109cc05?auto=format&fit=crop&w=1200&q=85' },
  { title: 'Ground Logistics', text: 'A connected first and last mile that keeps your supply chain in motion.', icon: Warehouse, tag: '02', image: 'https://images.unsplash.com/photo-1586528116311-ad8dd3c8310d?auto=format&fit=crop&w=1200&q=85' },
  { title: 'Charter & AOG', text: 'Specialist capacity and rapid response for the moments that matter.', icon: Globe2, tag: '03', image: 'https://images.unsplash.com/photo-1540962351504-03099e0a754b?auto=format&fit=crop&w=1200&q=85' }
]
const go = (id) => { menuOpen.value = false; document.getElementById(id)?.scrollIntoView({ behavior: 'smooth' }) }
const submitQuote = () => { submitted.value = true; setTimeout(() => { quoteOpen.value = false; submitted.value = false }, 2600) }
</script>

<template>
  <div class="page">
    <header class="nav" :class="{ 'is-open': menuOpen }">
      <a class="brand" href="#top" @click.prevent="go('top')"><span class="brand-mark">G</span><span>GESTAVIA</span></a>
      <nav class="desktop-links"><button @click="go('services')">What we do</button><button @click="go('network')">Where we operate</button><button @click="go('impact')">Sustainability</button><button @click="go('about')">Who we are</button></nav>
      <div class="nav-actions"><button class="text-link" @click="go('contact')">Contact</button><button class="quote-btn" @click="quoteOpen = true">Request a service <ArrowUpRight :size="16" /></button><button class="menu-toggle" aria-label="Toggle menu" @click="menuOpen = !menuOpen"><X v-if="menuOpen"/><Menu v-else/></button></div>
      <div v-if="menuOpen" class="mobile-menu"><button @click="go('services')">What we do <ArrowUpRight :size="17"/></button><button @click="go('network')">Where we operate <ArrowUpRight :size="17"/></button><button @click="go('impact')">Sustainability <ArrowUpRight :size="17"/></button><button @click="go('about')">Who we are <ArrowUpRight :size="17"/></button><button @click="quoteOpen = true; menuOpen = false">Request a service <ArrowUpRight :size="17"/></button></div>
    </header>

    <main id="top">
      <section class="hero">
        <div class="hero-image"></div><div class="hero-overlay"></div>
        <div class="hero-content reveal"><p class="eyebrow light">AVIATION · LOGISTICS · PURPOSE</p><h1>Move what<br/><em>matters.</em></h1><p class="hero-copy">We connect people, places and possibility through smarter aviation and logistics.</p><button class="circle-cta" @click="go('services')"><ArrowRight :size="21"/><span>Explore our services</span></button></div>
        <div class="hero-foot"><span>Gestavia / 2025</span><span class="scroll-note"><span class="scroll-line"></span>Scroll to discover</span><span>01 — 04</span></div>
      </section>

      <section id="about" class="intro section-pad"><div class="section-label">01 / OUR APPROACH</div><div class="intro-grid"><h2>Logistics that<br/><span>looks ahead.</span></h2><div><p class="lead">The world does not stand still. Neither do we.</p><p>Gestavia is an independent aviation and logistics partner for businesses that need to move further, faster and with intent. From a single shipment to a global operation, our people make complex feel simple.</p><button class="under-link" @click="go('network')">Meet Gestavia <ArrowUpRight :size="17"/></button></div></div></section>

      <section id="services" class="services section-pad"><div class="section-head"><div><div class="section-label">02 / WHAT WE DO</div><h2>One partner.<br/><span>Every move.</span></h2></div><p>Built around your needs, not a fixed template.</p></div><div class="service-layout"><div class="service-list"><button v-for="(service, i) in services" :key="service.title" class="service-item" :class="{active: activeService === i}" @click="activeService = i"><span class="service-number">{{ service.tag }}</span><span class="service-name">{{ service.title }}</span><ArrowRight :size="21"/></button></div><div class="service-visual"><img :src="services[activeService].image" :alt="services[activeService].title"/><div class="visual-caption"><component :is="services[activeService].icon" :size="21"/><span>{{ services[activeService].text }}</span></div></div></div></section>

      <section id="network" class="network"><div class="network-image"></div><div class="network-panel"><div class="section-label light">03 / GLOBAL REACH</div><h2>From here<br/><em>to anywhere.</em></h2><p>Our network brings local knowledge to global scale. Strategically located in Portugal, we connect Europe, Africa and the Americas every day.</p><div class="stats"><div><strong>34</strong><span>Countries served</span></div><div><strong>24/7</strong><span>Operations desk</span></div><div><strong>98%</strong><span>On-time delivery</span></div></div><button class="outline-btn" @click="quoteOpen = true">Plan your next move <ArrowUpRight :size="16"/></button></div></section>

      <section id="impact" class="impact section-pad"><div class="section-label">04 / OUR IMPACT</div><div class="impact-grid"><div><h2>A lighter<br/><span>footprint.</span></h2><p class="lead">Progress is measured in more than miles.</p></div><div class="impact-copy"><Leaf :size="31" stroke-width="1.4"/><p>We are working towards a more responsible future for aviation and logistics — from smarter routing and consolidated cargo to the everyday choices our teams make.</p><button class="under-link" @click="go('contact')">Our sustainability story <ArrowUpRight :size="17"/></button></div></div><div class="impact-banner"><span>2030</span><p>Our target: reduce operational emissions by 30%</p><div class="progress"><i></i></div></div></section>

      <section id="contact" class="contact"><div class="contact-inner"><div><div class="section-label light">LET'S CONNECT</div><h2>Ready when<br/><em>you are.</em></h2></div><div class="contact-right"><p>Tell us what needs moving. We will find the way forward.</p><button class="circle-cta dark" @click="quoteOpen = true"><ArrowRight :size="21"/><span>Request a service</span></button><div class="contact-details"><a href="mailto:ops@gestavia.com"><Mail :size="17"/>ops@gestavia.com</a><a href="tel:+351910224808"><Phone :size="17"/>+351 910 224 808</a></div></div></div></section>
    </main>

    <footer><div class="footer-top"><a class="brand" href="#top" @click.prevent="go('top')"><span class="brand-mark">G</span><span>GESTAVIA</span></a><p>Moving with purpose.</p><div class="socials"><a href="#" aria-label="LinkedIn"><Linkedin :size="17"/></a><a href="#" aria-label="Instagram"><Instagram :size="17"/></a></div></div><div class="footer-bottom"><span>© 2025 Gestavia Lda</span><span>R. Bartolomeu de Gusmão 118 · Portugal</span><span>Terms · Privacy</span></div></footer>

    <div v-if="quoteOpen" class="modal-backdrop" @click.self="quoteOpen = false"><div class="modal"><button class="modal-close" aria-label="Close" @click="quoteOpen = false"><X :size="21"/></button><template v-if="!submitted"><div class="section-label">REQUEST A SERVICE</div><h3>Let's move<br/><em>forward.</em></h3><p>Share a few details and our team will get back to you within one business day.</p><form @submit.prevent="submitQuote"><label>Name<input required placeholder="Your name"/></label><label>Work email<input type="email" required placeholder="you@company.com"/></label><label>How can we help?<select><option>Air freight</option><option>Ground logistics</option><option>Charter & AOG</option><option>Something else</option></select></label><button class="quote-btn full" type="submit">Send request <ArrowUpRight :size="16"/></button></form></template><template v-else><div class="success"><div class="success-icon"><Check :size="25"/></div><h3>Request received.</h3><p>Thank you. A Gestavia specialist will be in touch shortly.</p></div></template></div></div>
  </div>
</template>

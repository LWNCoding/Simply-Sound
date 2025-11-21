<script setup lang="ts">
import Layout from './components/Layout.vue'
import Carousel from './components/Carousel.vue'
import Reviews from './components/Reviews.vue'
import FullWidthImage from './components/FullWidthImage.vue'
import Introduction from './components/Introduction.vue'
import NewsletterSignup from './components/NewsletterSignup.vue'
import type { NavItem } from './components/NavBar.vue'
import type { ContactInfo, SocialLink, PaymentMethod } from './components/Footer.vue'
import type { CarouselItem } from './components/Carousel.vue'
import type { Review } from './components/Reviews.vue'

const carouselItems: CarouselItem[] = [
  {
    id: 1,
    image: 'public/images/image-1.jpg',
    title: 'Lorem ipsum',
    description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'
  },
  {
    id: 2,
    image: 'public/images/image-2.jpg',
    title: 'Lorem ipsum',
    description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'
  },
  {
    id: 3,
    image: 'public/images/image-3.jpg',
    title: 'Lorem ipsum',
    description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'
  },
  {
    id: 4,
    image: 'public/images/image-4.jpg',
    title: 'Lorem ipsum',
    description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'
  },
  {
    id: 5,
    image: 'public/images/image-5.jpg',
    title: 'Lorem ipsum',
    description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'
  },
  {
    id: 6,
    image: 'public/images/image-6.jpg',
    title: 'Lorem ipsum',
    description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'
  }
]

const navItems: NavItem[] = [
  { label: 'Home', path: '/' },
  { label: 'About', path: '/' },
  { label: 'Contact', path: '/' }
]

const contactInfo: ContactInfo[] = [
  { label: 'Email', value: 'simplysoundbyshannon@gmail.com', href: 'mailto:simplysoundbyshannon@gmail.com' },
  { label: 'Phone', value: '+447818616321', href: 'tel:+447818616321' },
  { label: 'Address', value: 'Simply Sound' }
]

const socialLinks: SocialLink[] = [
  { name: 'Instagram', url: 'https://www.instagram.com/simply_sound_by_shannon?igsh=MXZveWRsMjk4ejJnZQ%3D%3D&utm_source=qr' },
  { name: 'Facebook', url: 'https://www.facebook.com/share/16cYhChzkJ/?mibextid=wwXIfr' }
]

const paymentMethods: PaymentMethod[] = [
  { name: 'Visa' },
  { name: 'Mastercard' },
  { name: 'American Express' }
]

const reviews: Review[] = [
  {
    id: 1,
    name: 'Lorem ipsum',
    rating: 5,
    text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'
  },
  {
    id: 2,
    name: 'Lorem ipsum',
    rating: 5,
    text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'
  },
  {
    id: 3,
    name: 'Lorem ipsum',
    rating: 4.5,
    text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'
  },
  {
    id: 4,
    name: 'Lorem ipsum',
    rating: 5,
    text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'
  },
  {
    id: 5,
    name: 'Lorem ipsum',
    rating: 5,
    text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'
  }
]
</script>

<template>
  <Layout 
    name="Simply Sound" 
    :nav-items="navItems"
    :contact="contactInfo"
    :social-links="socialLinks"
    :payment-methods="paymentMethods"
  >
    <Introduction 
      title="ABOUT" 
      text="Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
      imagePath="public/images/profile.jpeg"
      imageAlt="Shannon - Simply Sound"
    />
    <FullWidthImage imagePath="public/images/banner_playing.png" />
    <Carousel title="SESSIONS" :items="carouselItems" />
    <NewsletterSignup />
    <Reviews title="CUSTOMER REVIEWS" :reviews="reviews" />
  </Layout>
</template>



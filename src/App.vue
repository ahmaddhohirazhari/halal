<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { 
  CheckCircleIcon, 
  ShieldCheckIcon, 
  DocumentCheckIcon,
  UserGroupIcon,
  PhoneIcon,
  EnvelopeIcon,
  MapPinIcon,
  StarIcon
} from '@heroicons/vue/24/solid'

const isVisible = ref(false)

onMounted(() => {
  isVisible.value = true
})

interface Package {
  id: number
  name: string
  price: string
  duration: string
  features: string[]
  popular?: boolean
}

const packages: Package[] = [
  {
    id: 1,
    name: "Paket Standar",
    price: "Rp 15.000.000",
    duration: "3-4 bulan",
    features: [
      "Audit sistem manajemen halal",
      "Pelatihan internal halal",
      "Pendampingan dokumentasi",
      "Sertifikat halal berlaku 4 tahun",
      "Konsultasi gratis selama masa berlaku"
    ]
  },
  {
    id: 2,
    name: "Paket Premium",
    price: "Rp 25.000.000",
    duration: "2-3 bulan",
    features: [
      "Fast track certification process",
      "Audit sistem manajemen halal",
      "Pelatihan internal & eksternal halal",
      "Pendampingan dokumentasi lengkap",
      "Sertifikat halal berlaku 4 tahun",
      "Konsultasi gratis selamanya",
      "Update regulasi terbaru"
    ],
    popular: true
  },
  {
    id: 3,
    name: "Paket Enterprise",
    price: "Rp 45.000.000",
    duration: "1-2 bulan",
    features: [
      "Priority fast track process",
      "Dedicated project manager",
      "Audit sistem manajemen halal",
      "Pelatihan komprehensif",
      "Pendampingan dokumentasi premium",
      "Sertifikat halal berlaku 4 tahun",
      "Konsultasi unlimited",
      "Maintenance & renewal assistance",
      "Marketing support materials"
    ]
  }
]

const testimonials = [
  {
    id: 1,
    name: "PT. Makanan Berkah",
    position: "Director",
    content: "Proses sertifikasi halal bersama tim ini sangat profesional dan efisien. Mereka membantu kami dari awal hingga akhir dengan sangat detail.",
    rating: 5
  },
  {
    id: 2,
    name: "CV. Rasa Nusantara",
    position: "Owner",
    content: "Pelayanan yang luar biasa! Tim sangat responsif dan membantu kami memahami setiap tahapan proses sertifikasi halal.",
    rating: 5
  },
  {
    id: 3,
    name: "UD. Sejahtera Food",
    position: "Manager",
    content: "Highly recommended! Proses cepat, harga kompetitif, dan hasil memuaskan. Produk kami sekarang sudah bersertifikat halal.",
    rating: 5
  }
]

const scrollToSection = (sectionId: string) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}

const openWhatsApp = (packageName?: string) => {
  const message = packageName 
    ? `Halo, saya tertarik dengan ${packageName} untuk sertifikasi halal. Bisa tolong berikan informasi lebih lanjut?`
    : `Halo, saya tertarik untuk mendapatkan sertifikasi halal untuk produk saya. Bisa tolong berikan informasi lebih lanjut?`
  
  const whatsappUrl = `https://wa.me/6281234567890?text=${encodeURIComponent(message)}`
  window.open(whatsappUrl, '_blank')
}
</script>

<template>
  <div class="min-h-screen bg-white">
    <!-- Navigation -->
    <nav class="fixed top-0 left-0 right-0 bg-white/95 backdrop-blur-sm shadow-sm z-50">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex justify-between items-center h-16">
          <div class="flex-shrink-0">
            <h1 class="text-xl font-bold text-gradient">HalalCert Indonesia</h1>
          </div>
          <div class="hidden md:block">
            <div class="ml-10 flex items-baseline space-x-4">
              <button @click="scrollToSection('beranda')" class="text-secondary-700 hover:text-primary-600 px-3 py-2 rounded-md text-sm font-medium transition-colors">
                Beranda
              </button>
              <button @click="scrollToSection('tentang')" class="text-secondary-700 hover:text-primary-600 px-3 py-2 rounded-md text-sm font-medium transition-colors">
                Tentang
              </button>
              <button @click="scrollToSection('paket')" class="text-secondary-700 hover:text-primary-600 px-3 py-2 rounded-md text-sm font-medium transition-colors">
                Paket
              </button>
              <button @click="scrollToSection('kontak')" class="text-secondary-700 hover:text-primary-600 px-3 py-2 rounded-md text-sm font-medium transition-colors">
                Kontak
              </button>
              <button @click="openWhatsApp()" class="bg-primary-600 text-white px-4 py-2 rounded-md text-sm font-medium hover:bg-primary-700 transition-colors">
                Konsultasi Gratis
              </button>
            </div>
          </div>
        </div>
      </div>
    </nav>

    <!-- Hero Section -->
    <section id="beranda" class="pt-16 section-padding gradient-bg text-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
          <div class="animate-slide-up">
            <h1 class="text-4xl md:text-6xl font-bold leading-tight mb-6">
              Sertifikasi Halal
              <span class="block text-blue-200">Terpercaya & Profesional</span>
            </h1>
            <p class="text-xl mb-8 text-blue-100 leading-relaxed">
              Dapatkan sertifikat halal untuk produk Anda dengan proses yang mudah, cepat, dan terpercaya. 
              Kami membantu bisnis Anda berkembang dengan jaminan halal yang diakui.
            </p>
            <div class="flex flex-col sm:flex-row gap-4">
              <button @click="openWhatsApp()" class="bg-white text-primary-600 px-8 py-4 rounded-lg font-semibold hover:bg-blue-50 transition-colors hover-lift">
                Konsultasi via WhatsApp
              </button>
              <button @click="scrollToSection('paket')" class="border-2 border-white text-white px-8 py-4 rounded-lg font-semibold hover:bg-white hover:text-primary-600 transition-colors">
                Lihat Paket Sertifikasi
              </button>
            </div>
          </div>
          <div class="animate-fade-in">
            <div class="bg-white/10 backdrop-blur-sm rounded-2xl p-8 hover-lift">
              <div class="grid grid-cols-2 gap-6">
                <div class="text-center">
                  <div class="text-3xl font-bold text-white mb-2">500+</div>
                  <div class="text-blue-200">Klien Terpusat</div>
                </div>
                <div class="text-center">
                  <div class="text-3xl font-bold text-white mb-2">100%</div>
                  <div class="text-blue-200">Tingkat Keberhasilan</div>
                </div>
                <div class="text-center">
                  <div class="text-3xl font-bold text-white mb-2">4 Tahun</div>
                  <div class="text-blue-200">Masa Berlaku</div>
                </div>
                <div class="text-center">
                  <div class="text-3xl font-bold text-white mb-2">24/7</div>
                  <div class="text-blue-200">Support</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <section id="tentang" class="section-padding bg-secondary-50">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="text-3xl md:text-4xl font-bold text-secondary-900 mb-6">
            Mengapa Memilih Kami?
          </h2>
          <p class="text-xl text-secondary-600 max-w-3xl mx-auto">
            Sebagai lembaga sertifikasi halal terpercaya, kami berkomitmen memberikan layanan terbaik 
            dengan standar internasional dan proses yang transparan.
          </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          <div class="bg-white rounded-xl p-6 shadow-sm hover-lift animate-slide-up">
            <div class="w-12 h-12 bg-primary-100 rounded-lg flex items-center justify-center mb-4">
              <ShieldCheckIcon class="h-6 w-6 text-primary-600" />
            </div>
            <h3 class="text-xl font-semibold text-secondary-900 mb-3">Terakreditasi Resmi</h3>
            <p class="text-secondary-600">
              Lembaga sertifikasi halal yang telah terakreditasi dan diakui secara nasional dan internasional.
            </p>
          </div>

          <div class="bg-white rounded-xl p-6 shadow-sm hover-lift animate-slide-up">
            <div class="w-12 h-12 bg-primary-100 rounded-lg flex items-center justify-center mb-4">
              <DocumentCheckIcon class="h-6 w-6 text-primary-600" />
            </div>
            <h3 class="text-xl font-semibold text-secondary-900 mb-3">Proses Mudah</h3>
            <p class="text-secondary-600">
              Proses sertifikasi yang mudah dipahami dengan pendampingan penuh dari tim ahli kami.
            </p>
          </div>

          <div class="bg-white rounded-xl p-6 shadow-sm hover-lift animate-slide-up">
            <div class="w-12 h-12 bg-primary-100 rounded-lg flex items-center justify-center mb-4">
              <UserGroupIcon class="h-6 w-6 text-primary-600" />
            </div>
            <h3 class="text-xl font-semibold text-secondary-900 mb-3">Tim Berpengalaman</h3>
            <p class="text-secondary-600">
              Didukung oleh tim auditor dan konsultan halal berpengalaman lebih dari 10 tahun.
            </p>
          </div>

          <div class="bg-white rounded-xl p-6 shadow-sm hover-lift animate-slide-up">
            <div class="w-12 h-12 bg-primary-100 rounded-lg flex items-center justify-center mb-4">
              <CheckCircleIcon class="h-6 w-6 text-primary-600" />
            </div>
            <h3 class="text-xl font-semibold text-secondary-900 mb-3">Jaminan Kepuasan</h3>
            <p class="text-secondary-600">
              100% jaminan kepuasan dengan after-sales support selama masa berlaku sertifikat.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- Packages Section -->
    <section id="paket" class="section-padding bg-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="text-3xl md:text-4xl font-bold text-secondary-900 mb-6">
            Paket Sertifikasi Halal
          </h2>
          <p class="text-xl text-secondary-600 max-w-3xl mx-auto">
            Pilih paket sertifikasi halal yang sesuai dengan kebutuhan bisnis Anda. 
            Semua paket sudah termasuk pendampingan lengkap hingga sertifikat terbit.
          </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div 
            v-for="pkg in packages" 
            :key="pkg.id"
            :class="[
              'bg-white rounded-2xl shadow-lg hover-lift animate-slide-up',
              pkg.popular ? 'ring-2 ring-primary-500 relative' : ''
            ]"
          >
            <div v-if="pkg.popular" class="absolute -top-4 left-1/2 transform -translate-x-1/2">
              <span class="bg-primary-500 text-white px-4 py-2 rounded-full text-sm font-semibold">
                Paling Populer
              </span>
            </div>
            
            <div class="p-8">
              <h3 class="text-2xl font-bold text-secondary-900 mb-2">{{ pkg.name }}</h3>
              <div class="text-3xl font-bold text-primary-600 mb-1">{{ pkg.price }}</div>
              <div class="text-secondary-500 mb-6">Estimasi: {{ pkg.duration }}</div>
              
              <ul class="space-y-3 mb-8">
                <li v-for="feature in pkg.features" :key="feature" class="flex items-start">
                  <CheckCircleIcon class="h-5 w-5 text-green-500 flex-shrink-0 mt-0.5 mr-3" />
                  <span class="text-secondary-700">{{ feature }}</span>
                </li>
              </ul>
              
              <button 
                @click="openWhatsApp(pkg.name)"
                :class="[
                  'w-full py-3 px-6 rounded-lg font-semibold transition-colors',
                  pkg.popular 
                    ? 'bg-primary-600 text-white hover:bg-primary-700' 
                    : 'bg-secondary-100 text-secondary-900 hover:bg-secondary-200'
                ]"
              >
                Pilih Paket Ini
              </button>
            </div>
          </div>
        </div>

        <div class="text-center mt-12">
          <p class="text-secondary-600 mb-4">
            Butuh paket khusus atau punya pertanyaan lain?
          </p>
          <button @click="openWhatsApp()" class="bg-primary-600 text-white px-8 py-3 rounded-lg font-semibold hover:bg-primary-700 transition-colors">
            Konsultasi Custom Package
          </button>
        </div>
      </div>
    </section>

    <!-- Testimonials Section -->
    <section class="section-padding bg-secondary-50">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="text-3xl md:text-4xl font-bold text-secondary-900 mb-6">
            Apa Kata Klien Kami
          </h2>
          <p class="text-xl text-secondary-600 max-w-3xl mx-auto">
            Kepercayaan klien adalah prioritas utama kami. Lihat pengalaman mereka yang telah 
            berhasil mendapatkan sertifikasi halal bersama kami.
          </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div 
            v-for="testimonial in testimonials" 
            :key="testimonial.id"
            class="bg-white rounded-xl p-6 shadow-sm hover-lift animate-slide-up"
          >
            <div class="flex items-center mb-4">
              <div v-for="i in testimonial.rating" :key="i">
                <StarIcon class="h-5 w-5 text-yellow-400" />
              </div>
            </div>
            <p class="text-secondary-700 mb-4 italic">
              "{{ testimonial.content }}"
            </p>
            <div class="border-t pt-4">
              <div class="font-semibold text-secondary-900">{{ testimonial.name }}</div>
              <div class="text-secondary-500 text-sm">{{ testimonial.position }}</div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="kontak" class="section-padding gradient-bg text-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="text-3xl md:text-4xl font-bold mb-6">
            Siap Memulai Sertifikasi Halal?
          </h2>
          <p class="text-xl text-blue-100 max-w-3xl mx-auto">
            Hubungi kami sekarang untuk konsultasi gratis dan mulai proses sertifikasi halal 
            untuk produk Anda. Tim ahli kami siap membantu 24/7.
          </p>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
          <div class="animate-slide-up">
            <h3 class="text-2xl font-bold mb-8">Informasi Kontak</h3>
            
            <div class="space-y-6">
              <div class="flex items-center">
                <div class="w-12 h-12 bg-white/20 rounded-lg flex items-center justify-center mr-4">
                  <PhoneIcon class="h-6 w-6 text-white" />
                </div>
                <div>
                  <div class="font-semibold">Telepon / WhatsApp</div>
                  <div class="text-blue-100">+62 812-3456-7890</div>
                </div>
              </div>

              <div class="flex items-center">
                <div class="w-12 h-12 bg-white/20 rounded-lg flex items-center justify-center mr-4">
                  <EnvelopeIcon class="h-6 w-6 text-white" />
                </div>
                <div>
                  <div class="font-semibold">Email</div>
                  <div class="text-blue-100">info@halalcert-indonesia.com</div>
                </div>
              </div>

              <div class="flex items-center">
                <div class="w-12 h-12 bg-white/20 rounded-lg flex items-center justify-center mr-4">
                  <MapPinIcon class="h-6 w-6 text-white" />
                </div>
                <div>
                  <div class="font-semibold">Alamat</div>
                  <div class="text-blue-100">
                    Jl. Sudirman No. 123, Jakarta Pusat<br>
                    DKI Jakarta 10110
                  </div>
                </div>
              </div>
            </div>
          </div>

          <div class="animate-slide-up">
            <div class="bg-white/10 backdrop-blur-sm rounded-2xl p-8">
              <h3 class="text-2xl font-bold mb-6">Konsultasi Gratis</h3>
              <p class="text-blue-100 mb-6">
                Dapatkan konsultasi gratis mengenai kebutuhan sertifikasi halal untuk produk Anda. 
                Klik tombol di bawah untuk langsung terhubung dengan tim ahli kami via WhatsApp.
              </p>
              
              <button 
                @click="openWhatsApp()"
                class="w-full bg-white text-primary-600 py-4 px-6 rounded-lg font-semibold hover:bg-blue-50 transition-colors hover-lift animate-bounce-gentle"
              >
                💬 Chat via WhatsApp Sekarang
              </button>
              
              <p class="text-blue-200 text-sm mt-4 text-center">
                Respon cepat dalam 5 menit • Konsultasi 100% gratis
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="bg-secondary-900 text-white py-12">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
          <div class="md:col-span-2">
            <h3 class="text-xl font-bold mb-4">HalalCert Indonesia</h3>
            <p class="text-secondary-300 mb-4">
              Lembaga sertifikasi halal terpercaya yang membantu bisnis Anda berkembang 
              dengan jaminan halal yang diakui secara nasional dan internasional.
            </p>
            <button @click="openWhatsApp()" class="bg-primary-600 text-white px-4 py-2 rounded-lg hover:bg-primary-700 transition-colors">
              Konsultasi Sekarang
            </button>
          </div>
          
          <div>
            <h4 class="font-semibold mb-4">Layanan</h4>
            <ul class="space-y-2 text-secondary-300">
              <li>Sertifikasi Halal</li>
              <li>Audit Sistem Halal</li>
              <li>Pelatihan Halal</li>
              <li>Konsultasi Halal</li>
            </ul>
          </div>
          
          <div>
            <h4 class="font-semibold mb-4">Informasi</h4>
            <ul class="space-y-2 text-secondary-300">
              <li>Tentang Kami</li>
              <li>Tim Ahli</li>
              <li>Sertifikat & Akreditasi</li>
              <li>FAQ</li>
            </ul>
          </div>
        </div>
        
        <div class="border-t border-secondary-700 mt-8 pt-8 text-center text-secondary-400">
          <p>&copy; 2024 HalalCert Indonesia. All rights reserved.</p>
        </div>
      </div>
    </footer>
  </div>
</template>
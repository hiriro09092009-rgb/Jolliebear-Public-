/**
 * Jolliebear Web Layout Interaction Script
 */

document.addEventListener('DOMContentLoaded', () => {
    
    // ==========================================
    // 1. MOBILE NAVIGATION TOGGLE
    // ==========================================
    const navToggle = document.querySelector('.mobile-nav-toggle');
    const navbar = document.querySelector('.navbar');
    const navLinks = document.querySelectorAll('.nav-link');

    if (navToggle && navbar) {
        navToggle.addEventListener('click', (e) => {
            e.stopPropagation();
            navbar.classList.toggle('open');
            const isOpen = navbar.classList.contains('open');
            navToggle.innerHTML = isOpen ? '<i class="fa-solid fa-xmark"></i>' : '<i class="fa-solid fa-bars"></i>';
        });

        // Close menu on link click
        navLinks.forEach(link => {
            link.addEventListener('click', () => {
                navbar.classList.remove('open');
                navToggle.innerHTML = '<i class="fa-solid fa-bars"></i>';
            });
        });

        // Close menu when clicking outside
        document.addEventListener('click', (e) => {
            if (!navbar.contains(e.target) && !navToggle.contains(e.target)) {
                navbar.classList.remove('open');
                navToggle.innerHTML = '<i class="fa-solid fa-bars"></i>';
            }
        });
    }

    // ==========================================
    // 2. HEADER SCROLL EFFECT
    // ==========================================
    const header = document.querySelector('.main-header');
    
    if (header) {
        window.addEventListener('scroll', () => {
            if (window.scrollY > 50) {
                header.classList.add('scrolled');
            } else {
                header.classList.remove('scrolled');
            }
        });
    }

    // ==========================================
    // 3. HERO CAROUSEL LOGIC
    // ==========================================
    const track = document.querySelector('.carousel-track');
    const slides = Array.from(document.querySelectorAll('.carousel-slide'));
    const indicators = Array.from(document.querySelectorAll('.carousel-indicator'));
    
    let currentSlideIndex = 0;
    let carouselInterval;
    const slideDuration = 5000; // 5 seconds

    const moveToSlide = (targetIndex) => {
        if (!slides.length) return;
        
        // Remove current classes
        slides[currentSlideIndex].classList.remove('current-slide');
        indicators[currentSlideIndex].classList.remove('current-slide-indicator');
        
        // Add classes to target
        slides[targetIndex].classList.add('current-slide');
        indicators[targetIndex].classList.add('current-slide-indicator');
        
        currentSlideIndex = targetIndex;
    };

    const startCarousel = () => {
        stopCarousel();
        carouselInterval = setInterval(() => {
            let nextIndex = (currentSlideIndex + 1) % slides.length;
            moveToSlide(nextIndex);
        }, slideDuration);
    };

    const stopCarousel = () => {
        if (carouselInterval) clearInterval(carouselInterval);
    };

    // Add click listeners to indicators
    indicators.forEach((indicator, index) => {
        indicator.addEventListener('click', () => {
            moveToSlide(index);
            startCarousel(); // Reset timer on manual navigation
        });
    });

    // Start auto slide
    if (slides.length > 0) {
        startCarousel();
        
        // Pause carousel when user hovers over the slider
        const heroSection = document.querySelector('.hero-carousel');
        if (heroSection) {
            heroSection.addEventListener('mouseenter', stopCarousel);
            heroSection.addEventListener('mouseleave', startCarousel);
        }
    }

    // ==========================================
    // 4. ORDER METHOD TOGGLE (Giao hàng / Đặt đến lấy)
    // ==========================================
    const deliveryToggle = document.getElementById('delivery-toggle');
    const pickupToggle = document.getElementById('pickup-toggle');
    const addressInput = document.getElementById('address-input');

    if (deliveryToggle && pickupToggle && addressInput) {
        deliveryToggle.addEventListener('click', () => {
            deliveryToggle.classList.add('active');
            pickupToggle.classList.remove('active');
            addressInput.placeholder = 'Nhập địa chỉ giao hàng của bạn...';
            // Focus input
            addressInput.focus();
        });

        pickupToggle.addEventListener('click', () => {
            pickupToggle.classList.add('active');
            deliveryToggle.classList.remove('active');
            addressInput.placeholder = 'Nhập địa chỉ cửa hàng hoặc khu vực muốn lấy hàng...';
            // Focus input
            addressInput.focus();
        });
    }

    // ==========================================
    // 5. LANGUAGE SELECTOR
    // ==========================================
    const langVi = document.getElementById('lang-vi');
    const langEn = document.getElementById('lang-en');

    if (langVi && langEn) {
        langVi.addEventListener('click', () => {
            langVi.classList.add('active');
            langEn.classList.remove('active');
            // Mock translation logic could go here
            console.log('Language switched to Vietnamese');
        });

        langEn.addEventListener('click', () => {
            langEn.classList.add('active');
            langVi.classList.remove('active');
            console.log('Language switched to English');
        });
    }

    // ==========================================
    // 6. COOKIE CONSENT BANNER
    // ==========================================
    const cookieBanner = document.getElementById('cookie-banner');
    const acceptBtn = document.getElementById('cookie-accept');
    const declineBtn = document.getElementById('cookie-decline');
    const settingsBtn = document.getElementById('cookie-settings');

    if (cookieBanner && acceptBtn && declineBtn) {
        // Show cookie banner after 1.5 seconds if consent not set
        const isConsentGiven = localStorage.getItem('cookie-consent');
        if (!isConsentGiven) {
            setTimeout(() => {
                cookieBanner.classList.add('show');
            }, 1500);
        }

        acceptBtn.addEventListener('click', () => {
            localStorage.setItem('cookie-consent', 'accepted');
            cookieBanner.classList.remove('show');
            console.log('Cookie consent accepted');
        });

        declineBtn.addEventListener('click', () => {
            localStorage.setItem('cookie-consent', 'declined');
            cookieBanner.classList.remove('show');
            console.log('Cookie consent declined');
        });

        if (settingsBtn) {
            settingsBtn.addEventListener('click', () => {
                alert('Tùy chỉnh cookie: Hệ thống sẽ tự động cấu hình các tùy chọn tối ưu nhất.');
                localStorage.setItem('cookie-consent', 'customized');
                cookieBanner.classList.remove('show');
            });
        }
    }
});

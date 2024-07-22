document.addEventListener('DOMContentLoaded', function () {
    function showTab(tabName) {
        var i, tabContent;
        tabContent = document.querySelectorAll('.tab-content');
        tabContent.forEach(function (content) {
            content.classList.remove('active');
        });
        document.querySelector('.tab-content.' + tabName).classList.add('active');
    }

    function changeSlide(n) {
        var slides = document.querySelectorAll('.slider .slides img');
        var currentSlide = Array.from(slides).findIndex(slide => slide.style.display === 'block');
        slides[currentSlide].style.display = 'none';
        var newSlide = (currentSlide + n + slides.length) % slides.length;
        slides[newSlide].style.display = 'block';
    }

    document.querySelectorAll('nav a').forEach(function (link) {
        link.addEventListener('click', function (e) {
            e.preventDefault();
            var tabName = e.target.getAttribute('onclick').split("'")[1];
            showTab(tabName);
        });
    });

    var sliderImages = document.querySelectorAll('.slider .slides img');
    sliderImages[0].style.display = 'block'; // Show the first image initially

    document.querySelector('.prev').addEventListener('click', function () {
        changeSlide(-1);
    });

    document.querySelector('.next').addEventListener('click', function () {
        changeSlide(1);
    });
});

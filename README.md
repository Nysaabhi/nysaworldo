<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Nysa Search Engine</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/Swiper/8.4.5/swiper-bundle.min.js"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/Swiper/8.4.5/swiper-bundle.min.css">
    <style>
:root {
    --primary-color: #3498db;
    --secondary-color: #2c3e50;
    --accent-color: #e74c3c;
    --text-color: #34495e;
    --border-color: #e0e0e0;
    --border-radius: 12px;
    --box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: 'Poppins', sans-serif;
    background-color: var(--background-color);
    color: var(--text-color);
    line-height: 1.6;
}

.container {
    max-width: 100%;
    margin: 0 auto;
    padding: 10px;
}

.header {
    padding: 20px;
    margin-bottom: 20px;
}

.heading {
    font-size: 4rem;
    font-weight: 700;
    text-align: center;
    margin-top: -25px;
    background: linear-gradient(45deg, #DA70D6, #FFC0CB);
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
    animation: gradientShift 10s ease infinite;
}

.subheading {
    text-align: center;
    font-size: 1.2rem;
    color: #57a;
    margin-top: 5px;
}

@keyframes gradientShift {
    0%, 100% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
}

.search-container {
    margin-bottom: 30px;
    position: relative;
    max-width: 100%;
    margin-left: auto;
    margin-right: auto;
}

.search-bar {
    width: 100%;
    height: 60px;
    padding: 15px 20px 15px 50px;
    font-size: 16px;
    border: 2px solid #000;
    border-radius: 50px;
    box-shadow: var(--box-shadow);
    transition: all 0.3s ease;
}

.search-bar:focus {
    outline: none;
    border-color: var(--primary-color);
    box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.2);
}

.search-icon {
    position: absolute;
    left: 20px;
    top: 50%;
    transform: translateY(-50%);
    color: #999;
    transition: color 0.3s ease;
}

.search-bar:focus + .search-icon {
    color: var(--primary-color);
}

.search-suggestions {
    position: absolute;
    top: calc(100% + 5px);
    left: 0;
    right: 0;
    background-color: white;
    border-radius: var(--border-radius);
    box-shadow: var(--box-shadow);
    z-index: 10;
    display: none;
    overflow: hidden;
}

.suggestion-item {
    padding: 12px 20px;
    cursor: pointer;
    transition: background-color 0.2s ease;
}

.suggestion-item:hover {
    background-color: #f5f5f5;
}

.filter-container {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    overflow-x: auto;
    white-space: nowrap;
    -webkit-overflow-scrolling: touch;
    scrollbar-width: none;
    -ms-overflow-style: none;
    padding: 20px 0;
    margin-bottom: 10px;
}

.filter-container::-webkit-scrollbar {
    display: none;
}

.filter-btn {
    padding: 20px 40px;
    font-size: 20px;
    font-weight: 600;
    border: none;
    border-radius: 60px;
    background-color: #f0f0f0;
    color: #333;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    margin-right: 20px;
    flex-shrink: 0;
    text-transform: uppercase;
    letter-spacing: 0.5px;
}

.filter-btn:hover {
    background-color: #e0e0e0;
    transform: translateY(-3px);
}

.filter-btn.active {
    background: linear-gradient(135deg, #3498db, #2980b9);
    color: white;
}

.filter-btn:focus {
    outline: none;
}

.separator-line {
    width: 100%;
    height: 1px;
    background-color: #e0e0e0;
    margin: 20px 0;
}

#cardsContainer {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 20px;
    margin-top: 20px;
}

.card {
    width: 100%;
    max-width: 350px;
    height: 600px;
    background-color: #ffffff;
    border-radius: 20px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.1);
    overflow: hidden;
    margin-bottom: 30px;
    display: flex;
    flex-direction: column;
}

.card-header {
    color: white;
    padding: 15px;
    position: relative;
    background-size: cover;
    border-radius: 12px 12px 0 0;
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

.header-content {
    display: flex;
    align-items: center;
    margin-bottom: 10px;
}

.logo {
    width: 50px;
    height: 50px;
    border-radius: 50%;
    background-color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 18px;
    font-weight: bold;
    box-shadow: 0 3px 10px rgba(0,0,0,0.2);
    margin-right: 15px;
}

.header-title {
    flex-grow: 1;
}

.title {
    font-size: 22px;
    font-weight: 700;
    margin-bottom: 2px;
}

.subtitle {
    font-size: 12px;
    font-weight: 500;
    opacity: 0.9;
}

.price-change, .birth-country {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 14px;
    margin-top: 5px;
}

.price, .change, .birth, .country-flag {
    font-weight: 600;
    background-color: rgba(255,255,255,0.2);
    padding: 3px 8px;
    border-radius: 10px;
}

.country-flag {
    font-size: 20px;
}

.details-swiper {
    height: 70px;
    padding: 10px 0;
}

.swiper-slide {
    padding: 0 8px;
}

.detail-box {
    border-radius: 10px;
    padding: 10px;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    box-shadow: 0 3px 10px rgba(0,0,0,0.1);
    cursor: pointer;
    position: relative;
}

.detail-title {
    font-weight: 600;
    margin-bottom: 3px;
    color: #ffffff;
    font-size: 12px;
}

.detail-content {
    font-size: 11px;
    color: #ffffff;
}

.chart-section, .image-carousel {
    padding: 10px;
    background-color: #f8f8f8;
    margin: 8px;
    border-radius: 8px;
    height: 285px;
    overflow: hidden;
}

.image-carousel img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 8px;
}

.button-group {
    margin-top: auto;
    display: flex;
    justify-content: space-between;
    padding: 10px;
}

.btn {
    flex: 1;
    margin: 0 2px;
    padding: 6px;
    border: none;
    border-radius: 6px;
    font-size: 10px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s ease;
    text-decoration: none;
    text-align: center;
}

.btn-primary {
    background: linear-gradient(135deg, #FFA500 0%, #FF4500 100%);
    color: white;
}

.btn-secondary {
    background-color: #fff5e6;
    color: #FFA500;
}

.btn:hover {
    transform: translateY(-1px);
    box-shadow: 0 3px 8px rgba(0,0,0,0.15);
}

.social-links {
    display: flex;
    justify-content: center;
    padding: 8px;
    border-top: 1px solid #ffe0b3;
}

.social-link {
    margin: 0 6px;
    color: #FFA500;
    font-size: 18px;
    transition: color 0.3s ease;
}

.social-link:hover {
    color: #FF4500;
}

.info-section {
    display: flex;
    justify-content: space-between;
    padding: 10px;
    font-size: 9px;
    color: #4a5568;
    background-color: #f8f8f8;
    border-top: 1px solid #e0e0e0;
}

.info-item {
    text-align: center;
    flex: 1;
}

.info-value {
    font-weight: 600;
    color: #2d3748;
    font-size: 10px;
}

.token-info, .nft-info, .web3-person-info, .contract-info,
.metaverse-info, .job-info, .education-info, .gig-info, 
.event-info, .concert-info, .insurance-info {
    display: flex;
    justify-content: space-between;
    padding: 6px 10px;
    font-size: 9px;
    color: #4a5568;
}

.token-info, .nft-info, .web3-person-info, .contract-info {
    background-color: #fff5e6;
}

.metaverse-info {
    background-color: #e6f7ff;
}

.job-info, .education-info, .gig-info, .event-info, .concert-info, .insurance-info {
    background-color: #f0f4f8;
}

.scrollable-description {
    height: 250px;
    overflow-y: auto;
    padding: 15px;
    background-color: #f8f8f8;
    border-radius: 8px;
    margin: 10px 0;
    font-size: 14px;
    line-height: 1.6;
    color: #4a5568;
}

.scrollable-description::-webkit-scrollbar {
    width: 8px;
}

.scrollable-description::-webkit-scrollbar-track {
    background: #f1f1f1;
    border-radius: 8px;
}

.scrollable-description::-webkit-scrollbar-thumb {
    background: #888;
    border-radius: 8px;
}

.scrollable-description::-webkit-scrollbar-thumb:hover {
    background: #555;
}

.company-info {
    display: flex;
    align-items: center;
    padding: 10px;
    background-color: #f8f8f8;
    border-top: 1px solid #e0e0e0;
}

.company-logo {
    width: 30px;
    height: 30px;
    border-radius: 50%;
    margin-right: 10px;
    object-fit: cover;
}

.company-details {
    flex-grow: 1;
}

.company-name {
    font-weight: 600;
    font-size: 12px;
}

.company-location {
    font-size: 10px;
    color: #666;
}

.notification-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
    opacity: 0;
    visibility: hidden;
    transition: opacity 0.3s ease, visibility 0.3s ease;
}

.notification-content {
    background-color: white;
    border-radius: 20px;
    padding: 20px;
    max-width: 80%;
    max-height: 80%;
    overflow-y: auto;
    box-shadow: 0 10px 30px rgba(0,0,0,0.2);
    transform: scale(0.9);
    transition: transform 0.3s ease;
}

.notification-overlay.active {
    opacity: 1;
    visibility: visible;
}

.notification-overlay.active .notification-content {
    transform: scale(1);
}

.notification-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 15px;
    padding-bottom: 10px;
    border-bottom: 1px solid #e0e0e0;
}

.notification-title {
    font-size: 18px;
    font-weight: 600;
    color: #333;
}

.notification-close {
    font-size: 24px;
    color: #999;
    cursor: pointer;
    transition: color 0.3s ease;
}

.notification-close:hover {
    color: #333;
}

.notification-body {
    font-size: 14px;
    line-height: 1.6;
    color: #666;
    max-height: 300px;
    overflow-y: auto;
}

@keyframes pulse {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.02); }
}

.pulse {
    animation: pulse 2s infinite;
}

.contract-code-container {
    height: 285px;
    background-color: #f8f8f8;
    border-radius: 8px;
    padding: 10px;
    margin: 10px 0;
    position: relative;
}

.contract-code {
    height: 100%;
    overflow-y: auto;
    font-family: monospace;
    white-space: pre-wrap;
    word-wrap: break-word;
    padding-right: 20px;
}

.contract-code pre {
    margin: 0;
}

.copy-icon {
    position: absolute;
    top: 10px;
    right: 10px;
    cursor: pointer;
    color: #666;
    transition: color 0.3s ease;
}

.copy-icon:hover {
    color: #333;
}

.copied-tooltip {
    position: absolute;
    background-color: #333;
    color: #fff;
    padding: 5px 10px;
    border-radius: 4px;
    font-size: 12px;
    top: -30px;
    right: 0;
    opacity: 0;
    transition: opacity 0.3s ease;
}

.copied-tooltip.show {
    opacity: 1;
}

.footer {
    background-color: var(--background-color);
    color: #000;
    padding: 20px 15px;
    position: relative;
    margin-top: auto;
}

.footer::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 4px;
    background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
}

.footer-container {
    max-width: 1200px;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
}

.footer-column {
    flex: 1;
    min-width: 200px;
    margin-bottom: 15px;
    padding: 0 10px;
}

.footer-logo {
    max-width: 120px;
    margin: 0 0 10px;
    transition: transform 0.3s ease;
}

.footer-logo:hover {
    transform: scale(1.05);
}

.footer-column h3 {
    margin: 0 0 8px;
    font-size: 1em;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 1px;
    position: relative;
    padding-bottom: 5px;
}

.footer-column h3::after {
    content: '';
    position: absolute;
    left: 0;
    bottom: 0;
    width: 30px;
    height: 2px;
    background-color: var(--secondary-color);
}

.footer-links {
    list-style: none;
    padding: 0;
    margin: 0;
}

.footer-links li {
    margin-bottom: 6px;
}

.footer-links a {
    color: #000;
    text-decoration: none;
    transition: color 0.3s ease, transform 0.3s ease;
    display: inline-block;
    font-size: 0.85em;
}

.footer-links a:hover {
    color: var(--primary-color);
    transform: translateX(3px);
}

.social-icons {
    display: flex;
    gap: 12px;
    margin-top: 15px;
}

.social-icons a {
    color: #000;
    font-size: 16px;
    transition: color 0.3s ease, transform 0.3s ease;
}

.social-icons a:hover {
    color: var(--primary-color);
    transform: scale(1.15);
}

.copyright {
    text-align: center;
    padding-top: 15px;
    margin-top: 15px;
    border-top: 1px solid var(--border-color);
    font-size: 0.75em;
}

@media (max-width: 768px) {
    .heading {
        font-size: 2.5rem;
    }

    .subheading {
        font-size: 0.9rem;
    }

    .search-bar {
        font-size: 14px;
        padding: 10px 10px 10px 35px;
    }

    .search-icon {
        left: 10px;
    }

    .filter-container {
        padding: 5px 0;
    }

    .filter-btn {
        padding: 8px 16px;
        font-size: 14px;
        margin-right: 10px;
    }

    .card {
        max-width: 100%;
        margin: 10px 0;
    }

    .title {
        font-size: 18px;
    }

    .subtitle {
        font-size: 10px;
    }

    .details-swiper {
        height: 60px;
    }

    .detail-box {
        padding: 8px;
    }

    .detail-title {
        font-size: 10px;
    }

    .detail-content {
        font-size: 9px;
    }

    .btn {
        font-size: 9px;
        padding: 5px;
    }

    .social-link {
        font-size: 16px;
    }

    .info-section {
        font-size: 8px;
    }

    .info-value {
        font-size: 9px;
    }

    .footer {
        padding: 15px 10px;
    }

    .footer-container {
        flex-direction: column;
    }

    .footer-column {
        width: 100%;
        text-align: center;
        padding: 0;
        margin-bottom: 15px;
    }

    .footer-column h3::after {
        left: 50%;
        transform: translateX(-50%);
    }

    .social-icons {
        justify-content: center;
    }

    .links-container {
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
        gap: 10px;
        margin-bottom: 10px;
    }

    .footer-column.links {
        flex: 0 0 calc(50% - 5px);
        text-align: left;
        margin-bottom: 0;
        padding: 0 5px;
        min-width: 0;
    }

    .footer-column.links h3 {
        font-size: 0.85em;
        margin-bottom: 6px;
        white-space: nowrap;
    }

    .footer-column.links h3::after {
        left: 0;
        transform: none;
        width: 20px;
    }

    .footer-links {
        padding-right: 5px;
    }

    .footer-links a {
        font-size: 0.75em;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
        display: block;
    }

    .footer-links li {
        margin-bottom: 3px;
    }

    .copyright {
        margin-top: 10px;
        padding-top: 10px;
    }
}

@media (min-width: 769px) and (max-width: 1024px) {
    .footer-column {
        flex: 0 0 calc(33.33% - 20px);
    }

    .filter-btn {
        padding: 12px 24px;
        font-size: 16px;
        margin-right: 15px;
    }
}

@media (min-width: 1025px) {
    .footer-column {
        flex: 0 0 calc(25% - 20px);
    }

    .filter-btn {
        padding: 20px 40px;
        font-size: 20px;
        margin-right: 20px;
    }
}
    </style>
</head>
<body>
    <main class="container">
        <header class="header">
            <h1 class="heading">
                <span id="n">N</span><span id="y">y</span><span id="s">s</span><span id="a">a</span>
            </h1>
            <p class="subheading">Innovate. Create. Inspire.</p>
        </header>
        <div class="search-container">
            <i class="fas fa-search search-icon"></i>
            <input type="text" class="search-bar" id="searchBar" placeholder="Search for cryptocurrencies, NFTs, people, or smart contracts...">
            <div class="search-suggestions" id="searchSuggestions"></div>
        </div>
        <div class="filter-container">
            <button class="filter-btn active" data-filter="all"><i class="fas fa-globe"></i> All</button>
            <button class="filter-btn" data-filter="crypto"><i class="fas fa-coins"></i> Crypto</button>
            <button class="filter-btn" data-filter="nft"><i class="fas fa-image"></i> NFT</button>
            <button class="filter-btn" data-filter="person"><i class="fas fa-user"></i> Web3 People</button>
            <button class="filter-btn" data-filter="event"><i class="fas fa-calendar-alt"></i> Events</button>
            <button class="filter-btn" data-filter="smart-contract"><i class="fas fa-file-code"></i> Smart Contracts</button>
            <button class="filter-btn" data-filter="metaverse"><i class="fas fa-vr-cardboard"></i> Metaverse</button>
<button class="filter-btn" data-filter="metaverse-concert">
  <i class="fas fa-music"></i> Concert
</button>
            <button class="filter-btn" data-filter="event"><i class="fas fa-calendar-alt"></i> Web3 Event</button>
            <button class="filter-btn" data-filter="crypto-insurance"><i class="fas fa-shield-alt"></i> Web3 Insurance</button>
        </div>
<div class="separator-line"></div>

        <div id="cardsContainer"></div>
    </main>

    <div class="notification-overlay" id="notificationOverlay">
        <div class="notification-content">
            <div class="notification-header">
                <h2 class="notification-title" id="notificationTitle"></h2>
                <span class="notification-close" id="notificationClose">&times;</span>
            </div>
            <div class="notification-body" id="notificationBody"></div>
        </div>
    </div>

    <footer class="footer">
        <div class="footer-container">
            <div class="footer-column">
                <img src="https://i.postimg.cc/Fz2XC6WH/Whats-App-Image-2024-08-19-at-06-13-30-1b87dd3a-removebg-preview.png" alt="Nysa Logo" class="footer-logo">
                <p>Explore, Create, Connect Unlock Infinite Possibilities with Nysa</p>
                <div class="social-icons">
                    <a href="#"><i class="fab fa-facebook"></i></a>
                    <a href="#"><i class="fab fa-twitter"></i></a>
                    <a href="#"><i class="fab fa-instagram"></i></a>
                    <a href="#"><i class="fab fa-linkedin"></i></a>
                    <a href="#"><i class="fab fa-youtube"></i></a>
                </div>
            </div>
            
            <div class="footer-column links">
                <h3>Quick Links</h3>
                <ul class="footer-links">
                    <li><a href="https://docs.google.com/forms/d/e/1FAIpQLSdVv1_mOUJwPjxlCKHccxyS2KyCxxBW2f1PnA5PcXopOToz-A/viewform?usp=sf_link">About Us</a></li>
                    <li><a href="#">Contact Us</a></li>
                    <li><a href="#">Privacy Policy</a></li>
                    <li><a href="#">Terms & Conditions</a></li>
                    <li><a href="mailto:info@nysa.com">Email Us</a></li>
                </ul>
            </div>
            
            <div class="footer-column links">
                <h3>Resources</h3>
                <ul class="footer-links">
                    <li><a href="#">Blog</a></li>
                    <li><a href="#">Tutorials</a></li>
                    <li><a href="#">FAQ</a></li>
                    <li><a href="#">Support</a></li>
                    <li><a href="#">API Documentation</a></li>
                </ul>
            </div>
        </div>
        
        <div class="copyright">
            &copy; 2024 Nysa Search Engine. All rights reserved.
        </div>
    </footer>


<script>
document.addEventListener('DOMContentLoaded', function() {
    const cardsContainer = document.getElementById('cardsContainer');
    const searchBar = document.getElementById('searchBar');
    const searchSuggestions = document.getElementById('searchSuggestions');
    const filterButtons = document.querySelectorAll('.filter-btn');

    let currentFilter = 'all';
    const CARDS_PER_CATEGORY = 3;

        const cardsData = [
    {
        elementId: 'bitcoin',
        logo: 'https://cryptologos.cc/logos/bitcoin-btc-logo.svg?v=035',
        title: 'Bitcoin',
        subtitle: 'Digital Gold',
        price: '$38,000',
        change: '+1.2%',
        gradient: 'linear-gradient(135deg, #F7931A 0%, #FFAB40 100%)',
        detailBoxes: [
            { 
                title: 'Overview', 
                content: 'Decentralized Digital Currency', 
                gradient: 'linear-gradient(135deg, #F7931A 0%, #FFAB40 100%)',
                fullDetails: `
                    <h3>Bitcoin Overview</h3>
                    <p>Bitcoin, created in 2009, is the first cryptocurrency with a limited supply of 21 million, offering secure, transparent, and decentralized transactions.</p>
                `
            },
            { 
                title: 'Technology', 
                content: 'Proof-of-Work Blockchain', 
                gradient: 'linear-gradient(135deg, #FF6B6B 0%, #FF8E53 100%)',
                fullDetails: `
                    <h3>Bitcoin Technology</h3>
                    <p>Bitcoin uses a Proof-of-Work consensus mechanism on a decentralized blockchain, secured by miners.</p>
                `
            },
            { 
                title: 'Adoption', 
                content: 'Growing Institutional Interest', 
                gradient: 'linear-gradient(135deg, #4E54C8 0%, #8F94FB 100%)',
                fullDetails: `
                    <h3>Bitcoin Adoption</h3>
                    <p>Bitcoin adoption is growing, with institutional investments, ETFs, and countries like El Salvador recognizing it as legal tender.</p>
                `
            }
        ],
        tokenInfo: [
            { label: 'Market Cap', value: '$580.5B' },
            { label: '24h Volume', value: '$15.2B' },
            { label: 'Circulating Supply', value: '19.4M BTC' }
        ],
        buttons: [
            { text: 'Buy', class: 'btn-primary' },
            { text: 'Trade', class: 'btn-secondary' },
            { text: 'Stake', class: 'btn-secondary' }
        ],
        socialLinks: [
            { icon: 'fab fa-twitter', url: '#' },
            { icon: 'fab fa-telegram', url: '#' },
            { icon: 'fab fa-github', url: '#' }
        ],
        tradingViewSymbol: "BITSTAMP:BTCUSD",
        type: 'crypto'
    },
    {
        elementId: 'ethereum',
        logo: 'https://cryptologos.cc/logos/ethereum-eth-logo.svg?v=025',
        title: 'Ethereum',
        subtitle: 'Dex Platform',
        price: '$2,800',
        change: '+2.5%',
        gradient: 'linear-gradient(135deg, #627EEA 0%, #8A9FF9 100%)',
        detailBoxes: [
            { 
                title: 'Overview', 
                content: 'Smart Contract Platform', 
                gradient: 'linear-gradient(135deg, #627EEA 0%, #8A9FF9 100%)',
                fullDetails: `
                    <h3>Ethereum Overview</h3>
                    <p>Ethereum is a decentralized, open-source blockchain platform that enables smart contracts and decentralized applications (dApps).</p>
                `
            },
            { 
                title: 'Technology', 
                content: 'Proof-of-Stake Blockchain', 
                gradient: 'linear-gradient(135deg, #FF6B6B 0%, #FF8E53 100%)',
                fullDetails: `
                    <h3>Ethereum Technology</h3>
                    <p>Ethereum transitioned from Proof-of-Work to Proof-of-Stake with the Merge, improving scalability and energy efficiency.</p>
                `
            },
            { 
                title: 'Ecosystem', 
                content: 'DeFi & NFT Hub', 
                gradient: 'linear-gradient(135deg, #4E54C8 0%, #8F94FB 100%)',
                fullDetails: `
                    <h3>Ethereum Ecosystem</h3>
                    <p>Ethereum hosts a vast ecosystem of decentralized finance (DeFi) applications, NFTs, and other blockchain-based solutions.</p>
                `
            }
        ],
        tokenInfo: [
            { label: 'Market Cap', value: '$320.5B' },
            { label: '24h Volume', value: '$12.7B' },
            { label: 'Circulating Supply', value: '120.2M ETH' }
        ],
        buttons: [
            { text: 'Buy', class: 'btn-primary' },
            { text: 'Trade', class: 'btn-secondary' },
            { text: 'Stake', class: 'btn-secondary' }
        ],
        socialLinks: [
            { icon: 'fab fa-twitter', url: '#' },
            { icon: 'fab fa-reddit', url: '#' },
            { icon: 'fab fa-github', url: '#' }
        ],
        tradingViewSymbol: "COINBASE:ETHUSD",
        type: 'crypto'
    },
    {
        elementId: 'binance-coin',
        logo: 'https://cryptologos.cc/logos/bnb-bnb-logo.svg?v=025',
        title: 'Binance',
        subtitle: 'Exchange Token',
        price: '$420',
        change: '+1.8%',
        gradient: 'linear-gradient(135deg, #F3BA2F 0%, #FFCE54 100%)',
        detailBoxes: [
            { 
                title: 'Overview', 
                content: 'Binance Ecosystem Token', 
                gradient: 'linear-gradient(135deg, #F3BA2F 0%, #FFCE54 100%)',
                fullDetails: `
                    <h3>Binance Coin Overview</h3>
                    <p>BNB is the native cryptocurrency of the Binance ecosystem, used for trading fee discounts and various utilities within the Binance Smart Chain.</p>
                `
            },
            { 
                title: 'Technology', 
                content: 'BEP-20 Token Standard', 
                gradient: 'linear-gradient(135deg, #FF6B6B 0%, #FF8E53 100%)',
                fullDetails: `
                    <h3>Binance Coin Technology</h3>
                    <p>BNB operates on the Binance Smart Chain, which is compatible with Ethereum Virtual Machine and supports smart contracts.</p>
                `
            },
            { 
                title: 'Use Cases', 
                content: 'Trading, DeFi, and More', 
                gradient: 'linear-gradient(135deg, #4E54C8 0%, #8F94FB 100%)',
                fullDetails: `
                    <h3>Binance Coin Use Cases</h3>
                    <p>BNB is used for trading fee discounts, participating in token sales, and as gas for transactions on the Binance Smart Chain.</p>
                `
            }
        ],
        tokenInfo: [
            { label: 'Market Cap', value: '$64.5B' },
            { label: '24h Volume', value: '$1.2B' },
            { label: 'Circulating Supply', value: '153.4M BNB' }
        ],
        buttons: [
            { text: 'Buy', class: 'btn-primary' },
            { text: 'Trade', class: 'btn-secondary' },
            { text: 'Stake', class: 'btn-secondary' }
        ],
        socialLinks: [
            { icon: 'fab fa-twitter', url: '#' },
            { icon: 'fab fa-telegram', url: '#' },
            { icon: 'fab fa-medium', url: '#' }
        ],
        tradingViewSymbol: "BINANCE:BNBUSD",
        type: 'crypto'
    },
    {
        elementId: 'cardano',
        logo: 'https://cryptologos.cc/logos/cardano-ada-logo.svg?v=025',
        title: 'Cardano',
        subtitle: 'Blockchain Platform',
        price: '$0.55',
        change: '+3.2%',
        gradient: 'linear-gradient(135deg, #0033AD 0%, #2A71D0 100%)',
        detailBoxes: [
            { 
                title: 'Overview', 
                content: 'Research-Driven Blockchain', 
                gradient: 'linear-gradient(135deg, #0033AD 0%, #2A71D0 100%)',
                fullDetails: `
                    <h3>Cardano Overview</h3>
                    <p>Cardano is a proof-of-stake blockchain platform that aims to provide a more sustainable, scalable, and transparent infrastructure for decentralized applications and cryptocurrencies.</p>
                `
            },
            { 
                title: 'Technology', 
                content: 'Ouroboros Consensus', 
                gradient: 'linear-gradient(135deg, #FF6B6B 0%, #FF8E53 100%)',
                fullDetails: `
                    <h3>Cardano Technology</h3>
                    <p>Cardano uses the Ouroboros proof-of-stake consensus mechanism, which is designed to be more energy-efficient than proof-of-work systems.</p>
                `
            },
            { 
                title: 'Development', 
                content: 'Peer-Reviewed Research', 
                gradient: 'linear-gradient(135deg, #4E54C8 0%, #8F94FB 100%)',
                fullDetails: `
                    <h3>Cardano Development</h3>
                    <p>Cardano's development is based on peer-reviewed research and follows a methodical, staged approach to implementing new features and upgrades.</p>
                `
            }
        ],
        tokenInfo: [
            { label: 'Market Cap', value: '$18.7B' },
            { label: '24h Volume', value: '$450M' },
            { label: 'Circulating Supply', value: '34B ADA' }
        ],
        buttons: [
            { text: 'Buy', class: 'btn-primary' },
            { text: 'Trade', class: 'btn-secondary' },
            { text: 'Stake', class: 'btn-secondary' }
        ],
        socialLinks: [
            { icon: 'fab fa-twitter', url: '#' },
            { icon: 'fab fa-reddit', url: '#' },
            { icon: 'fab fa-github', url: '#' }
        ],
        tradingViewSymbol: "BINANCE:ADAUSD",
        type: 'crypto'
    },
    {
        elementId: 'solana',
        logo: 'https://cryptologos.cc/logos/solana-sol-logo.svg?v=025',
        title: 'Solana',
        subtitle: 'High-Performance Blockchain',
        price: '$110',
        change: '+4.5%',
        gradient: 'linear-gradient(135deg, #00FFA3 0%, #03E1FF 100%)',
        detailBoxes: [
            { 
                title: 'Overview', 
                content: 'Fast & Scalable Platform', 
                gradient: 'linear-gradient(135deg, #00FFA3 0%, #03E1FF 100%)',
                fullDetails: `
                    <h3>Solana Overview</h3>
                    <p>Solana is a high-performance blockchain platform designed for decentralized apps and marketplaces, offering fast transaction speeds and low fees.</p>
                `
            },
            { 
                title: 'Technology', 
                content: 'Proof of History', 
                gradient: 'linear-gradient(135deg, #FF6B6B 0%, #FF8E53 100%)',
                fullDetails: `
                    <h3>Solana Technology</h3>
                    <p>Solana uses a unique Proof of History mechanism combined with Proof of Stake for consensus, enabling high throughput and scalability.</p>
                `
            },
            { 
                title: 'Ecosystem', 
                content: 'DeFi & NFT Projects', 
                gradient: 'linear-gradient(135deg, #4E54C8 0%, #8F94FB 100%)',
                fullDetails: `
                    <h3>Solana Ecosystem</h3>
                    <p>Solana hosts a growing ecosystem of DeFi applications, NFT marketplaces, and Web3 projects, attracting developers and users with its performance.</p>
                `
            }
        ],
        tokenInfo: [
            { label: 'Market Cap', value: '$42.5B' },
            { label: '24h Volume', value: '$1.8B' },
            { label: 'Circulating Supply', value: '386M SOL' }
        ],
        buttons: [
            { text: 'Buy', class: 'btn-primary' },
            { text: 'Trade', class: 'btn-secondary' },
            { text: 'Stake', class: 'btn-secondary' }
        ],
        socialLinks: [
            { icon: 'fab fa-twitter', url: '#' },
            { icon: 'fab fa-discord', url: '#' },
            { icon: 'fab fa-github', url: '#' }
        ],
        tradingViewSymbol: "BINANCE:SOLUSD",
        type: 'crypto'
    },
{
        elementId: 'polkadot',
        logo: 'https://cryptologos.cc/logos/polkadot-new-dot-logo.svg?v=025',
        title: 'Polkadot',
        subtitle: 'Multi-chain Network',
        price: '$7.80',
        change: '+2.1%',
        gradient: 'linear-gradient(135deg, #E6007A 0%, #FF4D8C 100%)',
        detailBoxes: [
            { 
                title: 'Overview', 
                content: 'Interoperable Blockchain', 
                gradient: 'linear-gradient(135deg, #E6007A 0%, #FF4D8C 100%)',
                fullDetails: `
                    <h3>Polkadot Overview</h3>
                    <p>Polkadot is a multi-chain network that enables interoperability between different blockchains, allowing for seamless data and asset transfers across chains.</p>
                `
            },
            { 
                title: 'Technology', 
                content: 'Parachain Architecture', 
                gradient: 'linear-gradient(135deg, #FF6B6B 0%, #FF8E53 100%)',
                fullDetails: `
                    <h3>Polkadot Technology</h3>
                    <p>Polkadot uses a unique parachain architecture, allowing multiple specialized blockchains to connect to a central relay chain for enhanced scalability and interoperability.</p>
                `
            },
            { 
                title: 'Governance', 
                content: 'On-chain Governance', 
                gradient: 'linear-gradient(135deg, #4E54C8 0%, #8F94FB 100%)',
                fullDetails: `
                    <h3>Polkadot Governance</h3>
                    <p>Polkadot implements on-chain governance, allowing DOT token holders to participate in decision-making processes for network upgrades and changes.</p>
                `
            }
        ],
        tokenInfo: [
            { label: 'Market Cap', value: '$9.2B' },
            { label: '24h Volume', value: '$320M' },
            { label: 'Circulating Supply', value: '1.18B DOT' }
        ],
        buttons: [
            { text: 'Buy', class: 'btn-primary' },
            { text: 'Trade', class: 'btn-secondary' },
            { text: 'Stake', class: 'btn-secondary' }
        ],
        socialLinks: [
            { icon: 'fab fa-twitter', url: '#' },
            { icon: 'fab fa-reddit', url: '#' },
            { icon: 'fab fa-github', url: '#' }
        ],
        tradingViewSymbol: "BINANCE:DOTUSD",
        type: 'crypto'
    },
    {
        elementId: 'ripple',
        logo: 'https://cryptologos.cc/logos/xrp-xrp-logo.svg?v=025',
        title: 'XRP',
        subtitle: 'Digital Payment Network',
        price: '$0.58',
        change: '+1.5%',
        gradient: 'linear-gradient(135deg, #23292F 0%, #384958 100%)',
        detailBoxes: [
            { 
                title: 'Overview', 
                content: 'Fast Global Payments', 
                gradient: 'linear-gradient(135deg, #23292F 0%, #384958 100%)',
                fullDetails: `
                    <h3>XRP Overview</h3>
                    <p>XRP is the native cryptocurrency of the XRP Ledger, designed to facilitate fast and cost-effective global money transfers and remittances.</p>
                `
            },
            { 
                title: 'Technology', 
                content: 'XRP Ledger Consensus', 
                gradient: 'linear-gradient(135deg, #FF6B6B 0%, #FF8E53 100%)',
                fullDetails: `
                    <h3>XRP Technology</h3>
                    <p>The XRP Ledger uses a unique consensus algorithm that allows for fast transaction confirmations without the need for mining.</p>
                `
            },
            { 
                title: 'Use Cases', 
                content: 'Cross-Border Payments', 
                gradient: 'linear-gradient(135deg, #4E54C8 0%, #8F94FB 100%)',
                fullDetails: `
                    <h3>XRP Use Cases</h3>
                    <p>XRP is primarily used for facilitating cross-border payments and as a bridge currency in Ripple's payment solutions for financial institutions.</p>
                `
            }
        ],
        tokenInfo: [
            { label: 'Market Cap', value: '$28.5B' },
            { label: '24h Volume', value: '$980M' },
            { label: 'Circulating Supply', value: '49.1B XRP' }
        ],
        buttons: [
            { text: 'Buy', class: 'btn-primary' },
            { text: 'Trade', class: 'btn-secondary' },
            { text: 'Learn More', class: 'btn-secondary' }
        ],
        socialLinks: [
            { icon: 'fab fa-twitter', url: '#' },
            { icon: 'fab fa-linkedin', url: '#' },
            { icon: 'fab fa-youtube', url: '#' }
        ],
        tradingViewSymbol: "BINANCE:XRPUSD",
        type: 'crypto'
    },
    {
        elementId: 'chainlink',
        logo: 'https://cryptologos.cc/logos/chainlink-link-logo.svg?v=025',
        title: 'Chainlink',
        subtitle: 'Decentralized Oracle Network',
        price: '$13.20',
        change: '+3.8%',
        gradient: 'linear-gradient(135deg, #2A5ADA 0%, #4D7FFF 100%)',
        detailBoxes: [
            { 
                title: 'Overview', 
                content: 'Blockchain Oracle Solution', 
                gradient: 'linear-gradient(135deg, #2A5ADA 0%, #4D7FFF 100%)',
                fullDetails: `
                    <h3>Chainlink Overview</h3>
                    <p>Chainlink is a decentralized oracle network that provides real-world data to smart contracts on various blockchain platforms, enabling more complex and useful applications.</p>
                `
            },
            { 
                title: 'Technology', 
                content: 'Decentralized Oracles', 
                gradient: 'linear-gradient(135deg, #FF6B6B 0%, #FF8E53 100%)',
                fullDetails: `
                    <h3>Chainlink Technology</h3>
                    <p>Chainlink uses a network of decentralized node operators to securely provide external data to blockchain networks, ensuring reliability and tamper-resistance.</p>
                `
            },
            { 
                title: 'Adoption', 
                content: 'Wide Integration', 
                gradient: 'linear-gradient(135deg, #4E54C8 0%, #8F94FB 100%)',
                fullDetails: `
                    <h3>Chainlink Adoption</h3>
                    <p>Chainlink has been widely adopted across various blockchain ecosystems, particularly in DeFi applications, for providing price feeds and other crucial off-chain data.</p>
                `
            }
        ],
        tokenInfo: [
            { label: 'Market Cap', value: '$6.8B' },
            { label: '24h Volume', value: '$410M' },
            { label: 'Circulating Supply', value: '517.1M LINK' }
        ],
        buttons: [
            { text: 'Buy', class: 'btn-primary' },
            { text: 'Trade', class: 'btn-secondary' },
            { text: 'Learn More', class: 'btn-secondary' }
        ],
        socialLinks: [
            { icon: 'fab fa-twitter', url: '#' },
            { label: 'Discord', icon: 'fab fa-discord', url: '#' },
            { icon: 'fab fa-youtube', url: '#' }
        ],
        tradingViewSymbol: "BINANCE:LINKUSD",
        type: 'crypto'
    },
    {
        elementId: 'uniswap',
        logo: 'https://cryptologos.cc/logos/uniswap-uni-logo.svg?v=025',
        title: 'Uniswap',
        subtitle: 'Decentralized Exchange Protocol',
        price: '$6.75',
        change: '+2.3%',
        gradient: 'linear-gradient(135deg, #FF007A 0%, #FF6A9C 100%)',
        detailBoxes: [
            { 
                title: 'Overview', 
                content: 'Automated Market Maker', 
                gradient: 'linear-gradient(135deg, #FF007A 0%, #FF6A9C 100%)',
                fullDetails: `
                    <h3>Uniswap Overview</h3>
                    <p>Uniswap is a leading decentralized exchange protocol on Ethereum, utilizing an automated market maker (AMM) model for token swaps without traditional order books.</p>
                `
            },
            { 
                title: 'Technology', 
                content: 'Constant Product Formula', 
                gradient: 'linear-gradient(135deg, #FF6B6B 0%, #FF8E53 100%)',
                fullDetails: `
                    <h3>Uniswap Technology</h3>
                    <p>Uniswap uses a constant product formula for its liquidity pools, allowing for efficient token swaps and providing opportunities for liquidity providers to earn fees.</p>
                `
            },
            { 
                title: 'Governance', 
                content: 'UNI Token Voting', 
                gradient: 'linear-gradient(135deg, #4E54C8 0%, #8F94FB 100%)',
                fullDetails: `
                    <h3>Uniswap Governance</h3>
                    <p>The UNI token allows holders to participate in governance decisions, voting on protocol upgrades, fee structures, and other important aspects of the Uniswap ecosystem.</p>
                `
            }
        ],
        tokenInfo: [
            { label: 'Market Cap', value: '$5.1B' },
            { label: '24h Volume', value: '$180M' },
            { label: 'Circulating Supply', value: '753.8M UNI' }
        ],
        buttons: [
            { text: 'Buy', class: 'btn-primary' },
            { text: 'Trade', class: 'btn-secondary' },
            { text: 'Provide Liquidity', class: 'btn-secondary' }
        ],
        socialLinks: [
            { icon: 'fab fa-twitter', url: '#' },
            { icon: 'fab fa-discord', url: '#' },
            { icon: 'fab fa-github', url: '#' }
        ],
        tradingViewSymbol: "BINANCE:UNIUSD",
        type: 'crypto'
    },
    {
        elementId: 'avalanche',
        logo: 'https://cryptologos.cc/logos/avalanche-avax-logo.svg?v=025',
        title: 'Avalanche',
        subtitle: 'High-Performance Blockchain Platform',
        price: '$35.80',
        change: '+4.2%',
        gradient: 'linear-gradient(135deg, #E84142 0%, #FF7276 100%)',
        detailBoxes: [
            { 
                title: 'Overview', 
                content: 'Scalable Smart Contract Platform', 
                gradient: 'linear-gradient(135deg, #E84142 0%, #FF7276 100%)',
                fullDetails: `
                    <h3>Avalanche Overview</h3>
                    <p>Avalanche is a layer-1 blockchain that aims to be fast, low-cost, and eco-friendly. It's designed to host decentralized applications and custom blockchain networks.</p>
                `
            },
            { 
                title: 'Technology', 
                content: 'Snowman Consensus Protocol', 
                gradient: 'linear-gradient(135deg, #FF6B6B 0%, #FF8E53 100%)',
                fullDetails: `
                    <h3>Avalanche Technology</h3>
                    <p>Avalanche uses a novel consensus protocol called Snowman, which allows for high throughput, fast finality, and strong security guarantees.</p>
                `
            },
            { 
                title: 'Ecosystem', 
                content: 'DeFi and dApp Development', 
                gradient: 'linear-gradient(135deg, #4E54C8 0%, #8F94FB 100%)',
                fullDetails: `
                    <h3>Avalanche Ecosystem</h3>
                    <p>Avalanche hosts a growing ecosystem of DeFi protocols, NFT platforms, and other decentralized applications, attracting developers with its high performance and Ethereum compatibility.</p>
                `
            }
        ],
        tokenInfo: [
            { label: 'Market Cap', value: '$12.5B' },
            { label: '24h Volume', value: '$520M' },
            { label: 'Circulating Supply', value: '349.3M AVAX' }
        ],
        buttons: [
            { text: 'Buy', class: 'btn-primary' },
            { text: 'Trade', class: 'btn-secondary' },
            { text: 'Stake', class: 'btn-secondary' }
        ],
        socialLinks: [
            { icon: 'fab fa-twitter', url: '#' },
            { icon: 'fab fa-telegram', url: '#' },
            { icon: 'fab fa-medium', url: '#' }
        ],
        tradingViewSymbol: "BINANCE:AVAXUSD",
        type: 'crypto'
    },
            {
                elementId: 'bored-ape',
                logo: 'BAYC',
                title: 'BAYC',
                subtitle: 'Exclusive NFT',
                price: '100 ETH',
                change: '+5.2%',
                gradient: 'linear-gradient(135deg, #FFD700 0%, #FFA500 100%)',
                detailBoxes: [
                    { 
                        title: 'Overview', 
                        content: 'Unique Ape Avatars', 
                        gradient: 'linear-gradient(135deg, #FFD700 0%, #FFA500 100%)',
                        fullDetails: `
                            <h3>BAYC Overview</h3>
                            <p>10,000 unique Bored Ape NFTs with commercial rights and exclusive community perks.</p>
                        `
                    },
                    { 
                        title: 'Rarity', 
                        content: 'Traits & Attributes', 
                        gradient: 'linear-gradient(135deg, #FF6B6B 0%, #FF8E53 100%)',
                        fullDetails: `
                            <h3>BAYC Rarity</h3>
                            <p>170+ traits like background, fur, eyes, and clothes determine rarity.</p>
                        `
                    },
                    { 
                        title: 'Community', 
                        content: 'Exclusive Benefits', 
                        gradient: 'linear-gradient(135deg, #4E54C8 0%, #8F94FB 100%)',
                        fullDetails: `
                            <h3>BAYC Community</h3>
                            <p>Access to exclusive merch, events, airdrops, and voting rights.</p>
                        `
                    }
                ],
                nftInfo: [
                    { label: 'Collection Size', value: '10,000' },
                    { label: 'Floor Price', value: '70 ETH' },
                    { label: 'Total Volume', value: '850K ETH' }
                ],
                buttons: [
                    { text: 'Buy', class: 'btn-primary' },
                    { text: 'OpenSea', class: 'btn-secondary' },
                    { text: 'Discord', class: 'btn-secondary' }
                ],
                socialLinks: [
                    { icon: 'fab fa-twitter', url: '#' },
                    { icon: 'fab fa-discord', url: '#' },
                    { icon: 'fab fa-instagram', url: '#' }
                ],
                nftImages: [
                    '/api/placeholder/400/320',
                    '/api/placeholder/400/320',
                    '/api/placeholder/400/320'
                ],
                type: 'nft'
            },
{
    elementId: "decentraland",
    type: "metaverse",
    logo: "MANA",
    title: "Decentraland",
    subtitle: "Virtual Real Estate Platform",
    price: "32,000 MANA",
    change: "+2.5%",
    gradient: "linear-gradient(135deg, #00b4d8 0%, #0077b6 100%)",
    detailBoxes: [
        {
            title: "Overview",
            content: "Virtual Land Parcels",
            gradient: "linear-gradient(135deg, #00b4d8 0%, #0077b6 100%)",
            fullDetails: "<h3>Decentraland</h3><p>Decentralized platform on Ethereum for owning virtual land and content.</p>"
        },
        {
            title: "Land Details",
            content: "Global Base, 20 LAND",
            gradient: "linear-gradient(135deg, #48cae4 0%, #0096c7 100%)",
            fullDetails: "<h3>Land Details</h3><ul><li>20 LAND parcels</li><li>Price: 32,000 MANA ($8,787.94)</li></ul>"
        },
        {
            title: "Market Info",
            content: "Stats & Figures",
            gradient: "linear-gradient(135deg, #0077b6 0%, #023e8a 100%)",
            fullDetails: "<h3>Market Info</h3><ul><li>Volume: 32,752 ETH</li><li>Floor Price: 0.115 ETH</li></ul>"
        }
    ],
    metaverseInfo: [
        { label: "Total LAND", value: "90,601" },
        { label: "Floor Price", value: "0.115 ETH" },
        { label: "Total Volume", value: "32,752 ETH" }
    ],
    buttons: [
        { text: "Buy", class: "btn-primary" },
        { text: "Explore", class: "btn-secondary" },
        { text: "Join Discord", class: "btn-secondary" }
    ],
    socialLinks: [
        { icon: "fab fa-twitter", url: "#" },
        { icon: "fab fa-discord", url: "#" },
        { icon: "fab fa-medium", url: "#" }
    ],
    metaverseImages: [
        "https://i.postimg.cc/sDhxdGz5/Whats-App-Image-2024-09-14-at-15-31-31-08e2595b.jpg"
    ],
    metaverseUrl: "https://decentraland.org/marketplace/contracts/0x959e104e1a4db6317fa58f8295f586e1a978c297/tokens/5760",
    type: 'metaverse'
},
            {
                elementId: 'vitalik-buterin',
                logo: '/api/placeholder/400/320',
                title: 'Vitalik Buterin',
                subtitle: 'Ethereum Co-Founder',
                birth: 'Jan 31, 1994',
                countryFlag: '🇷🇺',
                gradient: 'linear-gradient(135deg, #3498db 0%, #2980b9 100%)',
                detailBoxes: [
                    { 
                        title: 'Contribution', 
                        content: 'Created Ethereum', 
                        gradient: 'linear-gradient(135deg, #3498db 0%, #2980b9 100%)',
                        fullDetails: `
                            <h3>Contribution</h3>
                            <p>Co-founder of Ethereum, key Web3 figure.</p>
                        `
                    },
                    { 
                        title: 'Background', 
                        content: 'Computer Science', 
                        gradient: 'linear-gradient(135deg, #1abc9c 0%, #16a085 100%)',
                        fullDetails: `
                            <h3>Background</h3>
                            <ul><li>Born in 1994, Russia</li><li>Moved to Canada</li></ul>
                        `
                    },
                    { 
                        title: 'Vision', 
                        content: 'Decentralized Future', 
                        gradient: 'linear-gradient(135deg, #e74c3c 0%, #c0392b 100%)',
                        fullDetails: `
                            <h3>Vision</h3>
                            <p>Aims for a decentralized, open future.</p>
                        `
                    },
                ],
                personInfo: [
                    { label: 'Known for', value: 'Ethereum' },
                    { label: 'Nationality', value: 'Russian-Canadian' },
                    { label: 'Born', value: '1994' }
                ],
                buttons: [
                    { text: 'Follow', class: 'btn-primary' },
                    { text: 'Learn More', class: 'btn-secondary' }
                ],
                company: {
                    name: 'Ethereum Foundation',
                    location: 'Worldwide',
                    logo: '/api/placeholder/400/320'
                },
                socialLinks: [
                    { icon: 'fab fa-twitter', url: 'https://twitter.com/VitalikButerin' },
                    { icon: 'fab fa-github', url: 'https://github.com/vbuterin' },
                    { icon: 'fab fa-linkedin', url: 'https://www.linkedin.com/in/vitalik-buterin-267a7450/' },
                    { icon: 'fab fa-instagram', url: 'https://www.instagram.com/vitalik_buterin' }
                ],
                personImages: [
                    '/api/placeholder/400/320',
                    '/api/placeholder/400/320',
                    '/api/placeholder/400/320'
                ],
                type: 'person'
            },
{
    "elementId": "web3-metaverse-concert-card",
    "type": "metaverse-concert",
    "logo": "🎤",
    "title": "Virtual Concert: DJ Alchemy",
    "subtitle": "A Night of Decentralized Beats",
    "date": "December 12, 2024",
    "location": "Decentraland",
    "gradient": "linear-gradient(135deg, #d946ef 0%, #a21caf 100%)",
    "detailBoxes": [
        {
            "title": "Concert Overview",
            "content": "Experience a live DJ set in the metaverse.",
            "gradient": "linear-gradient(135deg, #d946ef 0%, #a21caf 100%)",
            "fullDetails": "<h3>Concert Overview</h3><p>DJ Alchemy brings a night of electrifying beats in the metaverse, streamed live from Decentraland. Join a global audience for this exclusive performance.</p>"
        },
        {
            "title": "Genres",
            "content": "Electronic, House, Future Bass",
            "gradient": "linear-gradient(135deg, #e879f9 0%, #d946ef 100%)",
            "fullDetails": "<h3>Genres</h3><ul><li>Electronic</li><li>House</li><li>Future Bass</li></ul>"
        },
        {
            "title": "Special Features",
            "content": "NFT Drops, Avatar Dance Battles",
            "gradient": "linear-gradient(135deg, #f472b6 0%, #ec4899 100%)",
            "fullDetails": "<h3>Special Features</h3><ul><li>Exclusive NFT Drops during the concert</li><li>Avatar dance battles with rewards</li></ul>"
        }
    ],
    "concertInfo": [
        { "label": "Date", "value": "December 12, 2024" },
        { "label": "Platform", "value": "Decentraland" },
        { "label": "Access", "value": "Free" }
    ],
    "buttons": [
        { "text": "Join Now", "class": "btn-primary" },
        { "text": "Learn More", "class": "btn-secondary" },
        { "text": "Save Event", "class": "btn-secondary" }
    ],
    "organization": {
        "name": "MetaBeats",
        "location": "Virtual",
        "logo": "/api/placeholder/400/320"
    },
    "socialLinks": [
        { "icon": "fab fa-linkedin", "url": "#" },
        { "icon": "fab fa-twitter", "url": "#" },
        { "icon": "fab fa-instagram", "url": "#" }
    ],
    "concertDescription": `
        <h2>About MetaBeats</h2>
        <p>MetaBeats is at the forefront of virtual entertainment, delivering immersive musical experiences in decentralized virtual worlds.</p>
        
        <h2>Concert Description</h2>
        <p>This exclusive DJ set by DJ Alchemy takes place in Decentraland's hottest virtual venue. With interactive features, NFT giveaways, and immersive visuals, this is not just a concert but a full metaverse experience.</p>
        
        <h2>What to Expect</h2>
        <ul>
            <li>Live streaming in high-fidelity 3D environments</li>
            <li>Exclusive NFT collectibles during the event</li>
            <li>Interactive avatar features and social spaces</li>
        </ul>

        <h2>How to Join</h2>
        <p>Connect to Decentraland using your wallet, and teleport into the event zone to experience the beats live!</p>
    `
},
            {
                type: 'smart-contract',
                elementId: 'erc20-token',
                title: 'ERC-20 Token',
                subtitle: 'Standard Ethereum Token Contract',
                logo: '📄',
                gradient: 'linear-gradient(135deg, #6e45e2 0%, #88d3ce 100%)',
            detailBoxes: [
                { title: 'Type', content: 'Tokenized Property', gradient: 'linear-gradient(135deg, #2c3e50 0%, #e67e22 100%)', tooltip: 'Represents ownership of a real estate property' },
                { title: 'Features', content: 'Fractional Ownership', gradient: 'linear-gradient(135deg, #e74c3c 0%, #e67e22 100%)', tooltip: 'Allows multiple investors to own shares of a property' },
                { title: 'Security', content: 'Escrow System', gradient: 'linear-gradient(135deg, #3498db 0%, #2980b9 100%)', tooltip: 'Secure transaction process with built-in escrow' },
                { title: 'Governance', content: 'DAO Enabled', gradient: 'linear-gradient(135deg, #9b59b6 0%, #8e44ad 100%)', tooltip: 'Decentralized decision making for property management' },
            ],
            contractInfo: [
                { label: 'Property ID', value: 'PROP-001' },
                { label: 'Total Shares', value: '1,000' },
                { label: 'Network', value: 'Ethereum' }
            ],
                contractCode: `pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20 {
    constructor(uint256 initialSupply) ERC20("MyToken", "MTK") {
        _mint(msg.sender, initialSupply);
    }
}`,
                buttons: [
                    { text: 'Contract', class: 'btn-primary' },
                    { text: 'Website', class: 'btn-secondary' },
                    { text: 'Etherscan', class: 'btn-secondary' }
                ],
                socialLinks: [
                    { url: '#', icon: 'fab fa-github' },
                    { url: '#', icon: 'fab fa-ethereum' }
                ],
                type: 'smart-contract'
            },
{
    elementId: "decentraland",
    type: "metaverse",
    logo: "MANA",
    title: "Decentraland",
    subtitle: "Virtual Real Estate Platform",
    price: "32,000 MANA",
    change: "+2.5%",
    gradient: "linear-gradient(135deg, #00b4d8 0%, #0077b6 100%)",
    detailBoxes: [
        {
            title: "Overview",
            content: "Virtual Land Parcels",
            gradient: "linear-gradient(135deg, #00b4d8 0%, #0077b6 100%)",
            fullDetails: "<h3>Decentraland</h3><p>Decentralized platform on Ethereum for owning virtual land and content.</p>"
        },
        {
            title: "Land Details",
            content: "Global Base, 20 LAND",
            gradient: "linear-gradient(135deg, #48cae4 0%, #0096c7 100%)",
            fullDetails: "<h3>Land Details</h3><ul><li>20 LAND parcels</li><li>Price: 32,000 MANA ($8,787.94)</li></ul>"
        },
        {
            title: "Market Info",
            content: "Stats & Figures",
            gradient: "linear-gradient(135deg, #0077b6 0%, #023e8a 100%)",
            fullDetails: "<h3>Market Info</h3><ul><li>Volume: 32,752 ETH</li><li>Floor Price: 0.115 ETH</li></ul>"
        }
    ],
    metaverseInfo: [
        { label: "Total LAND", value: "90,601" },
        { label: "Floor Price", value: "0.115 ETH" },
        { label: "Total Volume", value: "32,752 ETH" }
    ],
    buttons: [
        { text: "Buy", class: "btn-primary" },
        { text: "Explore", class: "btn-secondary" },
        { text: "Join Discord", class: "btn-secondary" }
    ],
    socialLinks: [
        { icon: "fab fa-twitter", url: "#" },
        { icon: "fab fa-discord", url: "#" },
        { icon: "fab fa-medium", url: "#" }
    ],
    metaverseImages: [
        "https://i.postimg.cc/sDhxdGz5/Whats-App-Image-2024-09-14-at-15-31-31-08e2595b.jpg"
    ],
    metaverseUrl: "https://decentraland.org/marketplace/contracts/0x959e104e1a4db6317fa58f8295f586e1a978c297/tokens/5760",
    type: 'metaverse'
},

  {
    elementId: "web3-developer-job",
    type: "job",
    logo: "👨‍💻",
    title: "Senior Web3 Developer",
    subtitle: "DeFi Protocol",
    salary: "$120,000 - $180,000",
    location: "Remote",
    gradient: "linear-gradient(135deg, #6366f1 0%, #a855f7 100%)",
    detailBoxes: [
        {
            title: "Overview",
            content: "Build DeFi Infrastructure",
            gradient: "linear-gradient(135deg, #6366f1 0%, #a855f7 100%)",
            fullDetails: "<h3>Job Overview</h3><p>Lead development of cutting-edge DeFi protocols and smart contracts.</p>"
        },
        {
            title: "Requirements",
            content: "Solidity, Web3.js, React",
            gradient: "linear-gradient(135deg, #8b5cf6 0%, #d946ef 100%)",
            fullDetails: "<h3>Key Requirements</h3><ul><li>5+ years in software development</li><li>3+ years Solidity experience</li><li>Strong knowledge of DeFi protocols</li></ul>"
        },
        {
            title: "Benefits",
            content: "Flexible Hours, Tokens",
            gradient: "linear-gradient(135deg, #a855f7 0%, #ec4899 100%)",
            fullDetails: "<h3>Benefits Package</h3><ul><li>Flexible working hours</li><li>Token-based incentives</li><li>Remote-first culture</li></ul>"
        }
    ],
    jobInfo: [
        { label: "Experience", value: "5+ years" },
        { label: "Employment", value: "Full-time" },
        { label: "Team Size", value: "10-20" }
    ],
    buttons: [
        { text: "Apply Now", class: "btn-primary" },
        { text: "Learn More", class: "btn-secondary" },
        { text: "Save Job", class: "btn-secondary" }
    ],
    company: {
        name: "DeFi Innovations Inc.",
        location: "Decentralized",
        logo: "/api/placeholder/400/320"
    },
    socialLinks: [
        { icon: "fab fa-linkedin", url: "#" },
        { icon: "fab fa-twitter", url: "#" },
        { icon: "fab fa-github", url: "#" }
    ],
    jobDescription: `
        <h2>About DeFi Innovations Inc.</h2>
        <p>We are at the forefront of decentralized finance, building the future of open, permissionless financial systems.</p>
        
        <h2>Job Description</h2>
        <p>As a Senior Web3 Developer, you will play a crucial role in designing, developing, and maintaining our DeFi protocols and smart contracts. You'll work closely with our product and security teams to deliver robust, scalable solutions.</p>
        
        <h2>Key Responsibilities</h2>
        <ul>
            <li>Develop and implement smart contracts for various DeFi applications</li>
            <li>Conduct code reviews and implement best practices for smart contract security</li>
            <li>Collaborate with the frontend team to integrate Web3 functionality</li>
            <li>Stay up-to-date with the latest developments in the Web3 and DeFi space</li>
        </ul>

        <h2>Qualifications</h2>
        <ul>
            <li>Bachelor's degree in Computer Science or related field</li>
            <li>5+ years of experience in software development</li>
            <li>3+ years of experience with Solidity and Ethereum development</li>
            <li>Strong understanding of DeFi concepts and protocols</li>
            <li>Experience with Web3.js, Ethers.js, and React</li>
            <li>Familiarity with testing frameworks like Truffle and Hardhat</li>
        </ul>

        <h2>How to Apply</h2>
        <p>If you're passionate about DeFi and want to work on groundbreaking projects, we'd love to hear from you. Please send your resume and a brief cover letter to careers@defiinnovations.com</p>
    `
},
{
    "elementId": "web3-event-card",
    "type": "event",
    "logo": "🎉",
    "title": "Blockchain Summit 2024",
    "subtitle": "The Future of Web3",
    "date": "March 15-17, 2024",
    "location": "New York, NY",
    "gradient": "linear-gradient(135deg, #3b82f6 0%, #1e40af 100%)",
    "detailBoxes": [
        {
            "title": "Event Overview",
            "content": "Explore the latest in blockchain technology and decentralized finance.",
            "gradient": "linear-gradient(135deg, #3b82f6 0%, #1e40af 100%)",
            "fullDetails": "<h3>Event Overview</h3><p>Join industry leaders, innovators, and enthusiasts to discuss the future of Web3 technologies.</p>"
        },
        {
            "title": "Speakers",
            "content": "Industry Experts from Ethereum, Polkadot, and more.",
            "gradient": "linear-gradient(135deg, #60a5fa 0%, #3b82f6 100%)",
            "fullDetails": "<h3>Key Speakers</h3><ul><li>Vitalik Buterin - Ethereum</li><li>Gavin Wood - Polkadot</li><li>Stani Kulechov - Aave</li></ul>"
        },
        {
            "title": "What You'll Learn",
            "content": "DeFi, NFTs, Web3 Governance",
            "gradient": "linear-gradient(135deg, #93c5fd 0%, #60a5fa 100%)",
            "fullDetails": "<h3>Key Topics</h3><ul><li>Decentralized Finance</li><li>Non-Fungible Tokens</li><li>Web3 Governance</li></ul>"
        }
    ],
    "eventInfo": [
        { "label": "Date", "value": "March 15-17, 2024" },
        { "label": "Location", "value": "New York, NY" },
        { "label": "Mode", "value": "In-Person & Virtual" }
    ],
    "buttons": [
        { "text": "Register Now", "class": "btn-primary" },
        { "text": "Learn More", "class": "btn-secondary" },
        { "text": "Save Event", "class": "btn-secondary" }
    ],
    "organization": {
        "name": "Blockchain Events Inc.",
        "location": "Global",
        "logo": "/api/placeholder/400/320"
    },
    "socialLinks": [
        { "icon": "fab fa-linkedin", "url": "#" },
        { "icon": "fab fa-twitter", "url": "#" },
        { "icon": "fab fa-github", "url": "#" }
    ],
    "eventDescription": `
        <h2>About Blockchain Events Inc.</h2>
        <p>Blockchain Events Inc. is the leading organizer of Web3 and blockchain conferences worldwide, with a focus on educating and connecting industry leaders.</p>
        
        <h2>Event Description</h2>
        <p>The Blockchain Summit 2024 will gather the best minds in blockchain, DeFi, and Web3. Whether you're an enthusiast, developer, or professional, this summit is the place to discuss and explore the cutting-edge developments in decentralized technology.</p>
        
        <h2>Key Highlights</h2>
        <ul>
            <li>Panel discussions with leading blockchain innovators</li>
            <li>Workshops on smart contracts, DeFi, and NFTs</li>
            <li>Networking opportunities with Web3 enthusiasts</li>
        </ul>

        <h2>How to Register</h2>
        <p>To attend the event, register on our website or join virtually from anywhere in the world.</p>
    `
},
{
    "elementId": "web3-gig-job-card",
    "type": "gig-job",
    "logo": "💼",
    "title": "Freelance Web3 Developer",
    "subtitle": "Smart Contract Development",
    "hourlyRate": "$50 - $100 per hour",
    "location": "Remote",
    "gradient": "linear-gradient(135deg, #f59e0b 0%, #d97706 100%)",
    "detailBoxes": [
        {
            "title": "Job Overview",
            "content": "Develop and audit smart contracts",
            "gradient": "linear-gradient(135deg, #f59e0b 0%, #d97706 100%)",
            "fullDetails": "<h3>Job Overview</h3><p>Work on decentralized projects and ensure the security and functionality of smart contracts on Ethereum and other blockchains.</p>"
        },
        {
            "title": "Skills Required",
            "content": "Solidity, Web3.js, Blockchain",
            "gradient": "linear-gradient(135deg, #fbbf24 0%, #f59e0b 100%)",
            "fullDetails": "<h3>Skills Required</h3><ul><li>Proficiency in Solidity for smart contract development</li><li>Experience with Web3.js and Ethereum</li><li>Strong problem-solving skills</li></ul>"
        },
        {
            "title": "What You'll Do",
            "content": "Smart Contract Development, DeFi Projects",
            "gradient": "linear-gradient(135deg, #fcd34d 0%, #fbbf24 100%)",
            "fullDetails": "<h3>Responsibilities</h3><ul><li>Develop and deploy smart contracts for decentralized applications</li><li>Participate in audits and code reviews</li><li>Collaborate with decentralized teams</li></ul>"
        }
    ],
    "gigInfo": [
        { "label": "Hourly Rate", "value": "$50 - $100 per hour" },
        { "label": "Level", "value": "Expert" },
        { "label": "Location", "value": "Remote" }
    ],
    "buttons": [
        { "text": "Apply Now", "class": "btn-primary" },
        { "text": "Learn More", "class": "btn-secondary" },
        { "text": "Save Job", "class": "btn-secondary" }
    ],
    "company": {
        "name": "DeFi Solutions",
        "location": "Decentralized",
        "logo": "/api/placeholder/400/320"
    },
    "socialLinks": [
        { "icon": "fab fa-linkedin", "url": "#" },
        { "icon": "fab fa-twitter", "url": "#" },
        { "icon": "fab fa-github", "url": "#" }
    ],
    "jobDescription": `
        <h2>About DeFi Solutions</h2>
        <p>DeFi Solutions is a leader in decentralized finance, offering innovative blockchain-based services and tools.</p>
        
        <h2>Job Description</h2>
        <p>As a freelance Web3 Developer, you'll work on a range of projects focused on developing and auditing smart contracts. You will play a key role in ensuring the functionality and security of decentralized applications.</p>
        
        <h2>Key Responsibilities</h2>
        <ul>
            <li>Develop, deploy, and audit smart contracts using Solidity</li>
            <li>Collaborate with cross-functional teams in a decentralized environment</li>
            <li>Conduct regular code reviews and implement best security practices</li>
        </ul>

        <h2>Required Skills</h2>
        <ul>
            <li>Advanced knowledge of Solidity and Web3.js</li>
            <li>Experience with Ethereum and decentralized applications (dApps)</li>
            <li>Strong understanding of DeFi protocols and smart contract security</li>
        </ul>

        <h2>How to Apply</h2>
        <p>If you're passionate about Web3 and decentralized finance, apply today by sending your resume and portfolio to jobs@defisolutions.com</p>
    `
},
{
    "elementId": "crypto-insurance-card",
    "type": "crypto-insurance",
    "logo": "🛡️",
    "title": "Crypto Asset Protection",
    "subtitle": "Insurance Coverage for Digital Assets",
    "coverage": "$100k - $1M",
    "location": "Global",
    "gradient": "linear-gradient(135deg, #6366f1 0%, #3b82f6 100%)",
    "detailBoxes": [
        {
            "title": "Policy Overview",
            "content": "Comprehensive crypto asset coverage",
            "gradient": "linear-gradient(135deg, #6366f1 0%, #3b82f6 100%)",
            "fullDetails": "<h3>Policy Overview</h3><p>Our policy covers theft, fraud, and exchange insolvency. Tailored specifically for protecting crypto holdings.</p>"
        },
        {
            "title": "What's Covered",
            "content": "Theft, Fraud, Hacking",
            "gradient": "linear-gradient(135deg, #818cf8 0%, #6366f1 100%)",
            "fullDetails": "<h3>Coverage Details</h3><ul><li>Theft and hacking incidents</li><li>Exchange insolvency coverage</li><li>Fraudulent activities protection</li></ul>"
        },
        {
            "title": "Why Choose Us",
            "content": "Global Coverage, Secure, Trusted",
            "gradient": "linear-gradient(135deg, #a5b4fc 0%, #818cf8 100%)",
            "fullDetails": "<h3>Why Choose Us</h3><ul><li>Global reach with trusted partners</li><li>Quick claim settlements</li><li>Secure your crypto with peace of mind</li></ul>"
        }
    ],
    "insuranceInfo": [
        { "label": "Coverage Amount", "value": "$100k - $1M" },
        { "label": "Provider", "value": "Blockchain Insurance Co." },
        { "label": "Location", "value": "Global" }
    ],
    "buttons": [
        { "text": "Get a Quote", "class": "btn-primary" },
        { "text": "Learn More", "class": "btn-secondary" },
        { "text": "Save Policy", "class": "btn-secondary" }
    ],
    "provider": {
        "name": "Blockchain Insurance Co.",
        "location": "Global",
        "logo": "/api/placeholder/400/320"
    },
    "socialLinks": [
        { "icon": "fab fa-linkedin", "url": "#" },
        { "icon": "fab fa-twitter", "url": "#" },
        { "icon": "fab fa-github", "url": "#" }
    ],
    "policyDescription": `
        <h2>About Blockchain Insurance Co.</h2>
        <p>Blockchain Insurance Co. offers comprehensive coverage for your digital assets, protecting against a wide range of risks including theft, fraud, and exchange insolvency.</p>
        
        <h2>Policy Details</h2>
        <p>Our insurance plan ensures your cryptocurrency holdings are safeguarded, allowing you to trade and invest with confidence.</p>
        
        <h2>What’s Covered</h2>
        <ul>
            <li>Theft due to hacking or breaches</li>
            <li>Loss due to exchange insolvency</li>
            <li>Fraudulent activities within the blockchain ecosystem</li>
        </ul>

        <h2>How to Apply</h2>
        <p>Get a personalized insurance quote today and secure your crypto assets by filling out our online form or contacting us directly.</p>
    `
},
{
    elementId: "web3-education-card",
    type: "education",
    logo: "🎓",
    title: "Master Web3 Development",
    subtitle: "Learn Blockchain and DeFi",
    courseDuration: "6 months",
    location: "Online",
    gradient: "linear-gradient(135deg, #34d399 0%, #10b981 100%)",
    detailBoxes: [
        {
            title: "Course Overview",
            content: "Become a Web3 expert",
            gradient: "linear-gradient(135deg, #34d399 0%, #10b981 100%)",
            fullDetails: "<h3>Course Overview</h3><p>Learn to develop decentralized applications (dApps) and smart contracts on blockchain platforms.</p>"
        },
        {
            title: "Prerequisites",
            content: "Basic JavaScript, Blockchain knowledge",
            gradient: "linear-gradient(135deg, #22c55e 0%, #16a34a 100%)",
            fullDetails: "<h3>Prerequisites</h3><ul><li>Basic understanding of JavaScript</li><li>Familiarity with blockchain fundamentals</li></ul>"
        },
        {
            title: "What You'll Learn",
            content: "Solidity, Smart Contracts, DeFi Protocols",
            gradient: "linear-gradient(135deg, #16a34a 0%, #059669 100%)",
            fullDetails: "<h3>Learning Outcomes</h3><ul><li>Write and deploy smart contracts using Solidity</li><li>Build dApps with Web3.js and React</li><li>Understand DeFi protocols and governance models</li></ul>"
        }
    ],
    courseInfo: [
        { label: "Duration", value: "6 months" },
        { label: "Level", value: "Intermediate" },
        { label: "Mode", value: "Online" }
    ],
    buttons: [
        { text: "Enroll Now", class: "btn-primary" },
        { text: "Learn More", class: "btn-secondary" },
        { text: "Save Course", class: "btn-secondary" }
    ],
    institution: {
        name: "Blockchain Academy",
        location: "Global",
        logo: "/api/placeholder/400/320"
    },
    socialLinks: [
        { icon: "fab fa-linkedin", url: "#" },
        { icon: "fab fa-twitter", url: "#" },
        { icon: "fab fa-github", url: "#" }
    ],
    courseDescription: `
        <h2>About Blockchain Academy</h2>
        <p>Blockchain Academy is a global institution focused on providing top-tier education in decentralized technologies, cryptocurrencies, and DeFi.</p>
        
        <h2>Course Description</h2>
        <p>This comprehensive course will equip you with the skills needed to build decentralized applications (dApps) and smart contracts on Ethereum and other blockchain platforms.</p>
        
        <h2>Modules Covered</h2>
        <ul>
            <li>Introduction to Blockchain and Web3</li>
            <li>Solidity Programming and Smart Contracts</li>
            <li>DeFi Protocols and dApp Development</li>
            <li>Testing and Security Best Practices</li>
        </ul>

        <h2>Certification</h2>
        <p>Upon completing the course, you'll receive a Blockchain Developer Certification.</p>
        
        <h2>How to Enroll</h2>
        <p>If you're ready to dive into the world of Web3 development, enroll today and start your journey into decentralized technologies.</p>
    `
},
            // ... (you can add more smart contract cards here) ...
        ];
        
function createCardHeader(data) {
    if (data.type === 'smart-contract') {
        return `
            <div class="card-header" style="background: ${data.gradient}">
                <div class="header-content">
                    <img src="${data.logo}" alt="${data.title}" class="logo" style="width: 50px; height: 50px; object-fit: cover;">
                    <div class="header-title">
                        <h2 class="title">${data.title}</h2>
                        <div class="subtitle">${data.subtitle}</div>
                    </div>
                </div>
            </div>
        `;
    }
if (data.type === 'crypto-insurance') {
    return `
        <div class="card-header" style="background: ${data.gradient}; border-radius: 12px;">
            <div class="header-content">
                <div class="logo" style="color: ${data.gradient.split(' ')[2]}">${data.logo}</div>
                <div class="header-title">
                    <h2 class="title">${data.title}</h2>
                    <div class="subtitle">${data.subtitle}</div>
                </div>
            </div>
            <div class="insurance-info">
                <span class="coverage">${data.coverage}</span>
                <span class="location">${data.location}</span>
            </div>
        </div>
    `;
}
if (data.type === 'metaverse-concert') {
    return `
        <div class="card-header" style="background: ${data.gradient}">
            <div class="header-content">
                    <img src="${data.logo}" alt="${data.title}" class="logo" style="width: 50px; height: 50px; object-fit: cover;">
                <div class="header-title">
                    <h2 class="title">${data.title}</h2>
                    <div class="subtitle">${data.subtitle}</div>
                </div>
            </div>
            <div class="concert-info">
                <span class="date">${data.date}</span>
                <span class="location">${data.location}</span>
            </div>
        </div>
    `;
}
if (data.type === 'event') {
    return `
        <div class="card-header" style="background: ${data.gradient}">
            <div class="header-content">
                    <img src="${data.logo}" alt="${data.title}" class="logo" style="width: 50px; height: 50px; object-fit: cover;">
                <div class="header-title">
                    <h2 class="title">${data.title}</h2>
                    <div class="subtitle">${data.subtitle}</div>
                </div>
            </div>
            <div class="event-info">
                <span class="date">${data.date}</span>
                <span class="location">${data.location}</span>
            </div>
        </div>
    `;
}
if (data.type === 'gig-job') {
    return `
        <div class="card-header" style="background: ${data.gradient}">
            <div class="header-content">
                    <img src="${data.logo}" alt="${data.title}" class="logo" style="width: 50px; height: 50px; object-fit: cover;">
                <div class="header-title">
                    <h2 class="title">${data.title}</h2>
                    <div class="subtitle">${data.subtitle}</div>
                </div>
            </div>
            <div class="gig-info">
                <span class="hourly-rate">${data.hourlyRate}</span>
                <span class="location">${data.location}</span>
            </div>
        </div>
    `;
}
if (data.type === 'education') {
    return `
        <div class="card-header" style="background: ${data.gradient}">
            <div class="header-content">
                    <img src="${data.logo}" alt="${data.title}" class="logo" style="width: 50px; height: 50px; object-fit: cover;">
                <div class="header-title">
                    <h2 class="title">${data.title}</h2>
                    <div class="subtitle">${data.subtitle}</div>
                </div>
            </div>
            <div class="education-info">
                <span class="course-duration">${data.courseDuration}</span>
                <span class="location">${data.location}</span>
            </div>
        </div>
    `;
}
if (data.type === 'job') {
    return `
        <div class="card-header" style="background: ${data.gradient}">
            <div class="header-content">
                    <img src="${data.logo}" alt="${data.title}" class="logo" style="width: 50px; height: 50px; object-fit: cover;">
                <div class="header-title">
                    <h2 class="title">${data.title}</h2>
                    <div class="subtitle">${data.subtitle}</div>
                </div>
            </div>
            <div class="job-info">
                <span class="salary">${data.salary}</span>
                <span class="location">${data.location}</span>
            </div>
        </div>
    `;
}
    if (data.type === 'person') {
        return `
            <div class="card-header" style="background: ${data.gradient}">
                <div class="header-content">
                    <img src="${data.logo}" alt="${data.title}" class="logo" style="width: 50px; height: 50px; object-fit: cover;">
                    <div class="header-title">
                        <h2 class="title">${data.title}</h2>
                        <div class="subtitle">${data.subtitle}</div>
                    </div>
                </div>
                <div class="birth-country">
                    <span class="birth">${data.birth}</span>
                    <span class="country-flag">${data.countryFlag}</span>
                </div>
            </div>
        `;
    }
    if (data.type === 'metaverse') {
        return `
            <div class="card-header" style="background: ${data.gradient}">
                <div class="header-content">
                    <img src="${data.logo}" alt="${data.title}" class="logo" style="width: 50px; height: 50px; object-fit: cover;">
                    <div class="header-title">
                        <h2 class="title">${data.title}</h2>
                        <div class="subtitle">${data.subtitle}</div>
                    </div>
                </div>
                <div class="price-change">
                    <span class="price">${data.price}</span>
                    <span class="change">${data.change}</span>
                </div>
            </div>
        `;
    }
    return `
        <div class="card-header" style="background: ${data.gradient}">
            <div class="header-content">
                    <img src="${data.logo}" alt="${data.title}" class="logo" style="width: 50px; height: 50px; object-fit: cover;">
                <div class="header-title">
                    <h2 class="title">${data.title}</h2>
                    <div class="subtitle">${data.subtitle}</div>
                </div>
            </div>
            ${data.price ? `
            <div class="price-change">
                <span class="price">${data.price}</span>
                <span class="change">${data.change}</span>
            </div>
            ` : ''}
        </div>
    `;
}

function createDetailBoxes(data) {
    return `
        <div class="details-swiper">
            <div class="swiper-wrapper">
                ${data.detailBoxes.map((box, index) => `
                    <div class="swiper-slide">
                        <div class="detail-box" style="background: ${box.gradient};" data-card-id="${data.elementId}" data-detail-index="${index}">
                            <div class="detail-title">${box.title}</div>
                            <div class="detail-content">${box.content}</div>
                        </div>
                    </div>
                `).join('')}
            </div>
        </div>
    `;
}

function createTokenInfo(data) {
    if (data.type === 'smart-contract') {
        return `
            <div class="contract-info">
                ${data.contractInfo.map(info => `
                    <div class="contract-info-item">
                        <div>${info.label}</div>
                        <div class="contract-info-value">${info.value}</div>
                    </div>
                `).join('')}
            </div>
        `;
    }
if (data.type === 'crypto-insurance') {
    return `
        <div class="insurance-info">
            ${data.insuranceInfo.map(info => `
                <div class="insurance-info-item">
                    <div>${info.label}</div>
                    <div class="insurance-info-value">${info.value}</div>
                </div>
            `).join('')}
        </div>
    `;
}
if (data.type === 'event') {
    return `
        <div class="event-info">
            ${data.eventInfo.map(info => `
                <div class="event-info-item">
                    <div>${info.label}</div>
                    <div class="event-info-value">${info.value}</div>
                </div>
            `).join('')}
        </div>
    `;
}
if (data.type === 'gig-job') {
    return `
        <div class="gig-info">
            ${data.gigInfo.map(info => `
                <div class="gig-info-item">
                    <div>${info.label}</div>
                    <div class="gig-info-value">${info.value}</div>
                </div>
            `).join('')}
        </div>
    `;
}
if (data.type === 'metaverse-concert') {
    return `
        <div class="concert-info">
            ${data.concertInfo.map(info => `
                <div class="concert-info-item">
                    <div>${info.label}</div>
                    <div class="concert-info-value">${info.value}</div>
                </div>
            `).join('')}
        </div>
    `;
}
if (data.type === 'education') {
    return `
        <div class="education-info">
            ${data.courseInfo.map(info => `
                <div class="education-info-item">
                    <div>${info.label}</div>
                    <div class="education-info-value">${info.value}</div>
                </div>
            `).join('')}
        </div>
    `;
}
if (data.type === 'job') {
    return `
        <div class="job-info">
            ${data.jobInfo.map(info => `
                <div class="job-info-item">
                    <div>${info.label}</div>
                    <div class="job-info-value">${info.value}</div>
                </div>
            `).join('')}
        </div>
    `;
}
    if (data.type === 'person') {
        return `
            <div class="web3-person-info">
                ${data.personInfo.map(info => `
                    <div class="web3-person-info-item">
                        <div>${info.label}</div>
                        <div class="web3-person-info-value">${info.value}</div>
                    </div>
                `).join('')}
            </div>
        `;
    }
    if (data.type === 'metaverse') {
        return `
            <div class="metaverse-info">
                ${data.metaverseInfo.map(info => `
                    <div class="metaverse-info-item">
                        <div>${info.label}</div>
                        <div class="metaverse-info-value">${info.value}</div>
                    </div>
                `).join('')}
            </div>
        `;
    }
    const infoData = data.type === 'crypto' ? data.tokenInfo : data.nftInfo;
    return `
        <div class="${data.type === 'crypto' ? 'token-info' : 'nft-info'}">
            ${infoData.map(info => `
                <div class="${data.type === 'crypto' ? 'token-info-item' : 'nft-info-item'}">
                    <div>${info.label}</div>
                    <div class="${data.type === 'crypto' ? 'token-info-value' : 'nft-info-value'}">${info.value}</div>
                </div>
            `).join('')}
        </div>
    `;
}

        function createChartSection(data) {
            if (data.type === 'smart-contract') {
                return `
                    <div class="contract-code-container">
                        <div class="contract-code">
                            <i class="fas fa-copy copy-icon" onclick="copyContractCode('${data.elementId}')"></i>
                            <div class="copied-tooltip">Copied!</div>
                            <pre><code>${data.contractCode}</code></pre>
                        </div>
                    </div>
                `;
            }
            if (data.type === 'crypto-insurance') {
                return `
                    <div class="scrollable-description">
                        ${data.policyDescription}
                    </div>
                `;
            }
            if (data.type === 'metaverse-concert') {
                return `
                    <div class="scrollable-description">
                        ${data.concertDescription}
                    </div>
                `;
            }
            if (data.type === 'gig-job') {
                return `
                    <div class="scrollable-description">
                        ${data.jobDescription}
                    </div>
                `;
            }
            if (data.type === 'event') {
                return `
                    <div class="scrollable-description">
                        ${data.eventDescription}
                    </div>
                `;
            }
            if (data.type === 'education') {
                return `
                    <div class="scrollable-description">
                        ${data.courseDescription}
                    </div>
                `;
            }
            if (data.type === 'job') {
                return `
                    <div class="scrollable-description">
                        ${data.jobDescription}
                    </div>
                `;
            }
            if (data.type === 'person') {
                return `
                    <div class="image-carousel">
                        <div class="swiper-wrapper">
                            ${data.personImages.map(img => `
                                <div class="swiper-slide">
                                    <img src="${img}" alt="Person Image">
                                </div>
                            `).join('')}
                        </div>
                    </div>
                `;
            } else if (data.type === 'crypto') {
                return `
                    <div class="chart-section">
                        <div id="${data.elementId}-tv-chart-container" style="height: 100%;"></div>
                    </div>
                `;
            } else if (data.type === 'nft') {
                return `
                    <div class="image-carousel">
                        <div class="swiper-wrapper">
                            ${data.nftImages.map(img => `
                                <div class="swiper-slide">
                                    <img src="${img}" alt="NFT Image">
                                </div>
                            `).join('')}
                        </div>
                    </div>
                `;
            } else if (data.type === 'metaverse') {
                return `
                    <div class="image-carousel">
                        <div class="swiper-wrapper">
                            ${data.metaverseImages.map(img => `
                                <div class="swiper-slide">
                                    <img src="${img}" alt="Metaverse Image">
                                </div>
                            `).join('')}
                        </div>
                    </div>
                `;
            }
        }

function createButtonGroup(data) {
    return `
        <div class="button-group">
            ${data.buttons.map(button => `
                <a href="#" class="btn ${button.class}" style="${button.class === 'btn-primary' ? `background: ${data.gradient};` : `color: ${data.gradient.split(' ')[2]};`}" onclick="showNotification('${data.title}', '${button.text}')">${button.text}</a>
            `).join('')}
        </div>
    `;
}

function createSocialLinks(data) {
    return `
        <div class="social-links">
            ${data.socialLinks.map(link => `
                <a href="${link.url}" class="social-link" style="color: ${data.gradient.split(' ')[2]};"><i class="${link.icon}"></i></a>
            `).join('')}
        </div>
    `;
}

function renderCard(data) {
    const cardHTML = `
        <div class="card" id="${data.elementId}">
            ${createCardHeader(data)}
            ${createDetailBoxes(data)}
            ${createTokenInfo(data)}
            ${createChartSection(data)}
            ${createButtonGroup(data)}
            ${createSocialLinks(data)}
        </div>
    `;
    cardsContainer.insertAdjacentHTML('beforeend', cardHTML);
}

function initializeTradingViewWidget(cardData) {
    if (cardData.type === 'crypto') {
        const container = document.getElementById(`${cardData.elementId}-tv-chart-container`);
        if (container) {
            new TradingView.widget({
                "width": "100%",
                "height": 300,
                "symbol": cardData.tradingViewSymbol,
                "interval": "D",
                "timezone": "Etc/UTC",
                "theme": "light",
                "style": "1",
                "locale": "en",
                "toolbar_bg": "#f1f3f6",
                "enable_publishing": false,
                "allow_symbol_change": true,
                "container_id": `${cardData.elementId}-tv-chart-container`
            });
        }
    }
}

    function renderCards(filteredData = cardsData) {
        cardsContainer.innerHTML = '';
        let cardsToRender = filteredData;

        if (currentFilter === 'all') {
            const categoryCounts = {};
            cardsToRender = filteredData.filter(card => {
                if (!categoryCounts[card.type]) {
                    categoryCounts[card.type] = 0;
                }
                if (categoryCounts[card.type] < CARDS_PER_CATEGORY) {
                    categoryCounts[card.type]++;
                    return true;
                }
                return false;
            });
        }

        cardsToRender.forEach(cardData => {
            renderCard(cardData);

            // Initialize Swiper for detail boxes
            new Swiper(`#${cardData.elementId} .details-swiper`, {
                direction: 'horizontal',
                loop: true,
                slidesPerView: 1.2,
                spaceBetween: 10,
                centeredSlides: true,
                autoplay: {
                    delay: 3000,
                    disableOnInteraction: false,
                },
            });

            if (cardData.type === 'nft' || cardData.type === 'person' || cardData.type === 'metaverse') {
                // Initialize Swiper for NFT, person, and metaverse carousel
                new Swiper(`#${cardData.elementId} .image-carousel`, {
                    direction: 'horizontal',
                    loop: true,
                    slidesPerView: 1,
                    spaceBetween: 10,
                    centeredSlides: true,
                    autoplay: {
                        delay: 5000,
                        disableOnInteraction: false,
                    },
                });
            } else if (cardData.type === 'crypto') {
initializeTradingViewWidget(cardData);
            }

            const detailBoxes = document.querySelectorAll(`#${cardData.elementId} .detail-box`);
            detailBoxes.forEach(box => {
                box.addEventListener('click', function() {
                    const cardId = this.getAttribute('data-card-id');
                    const detailIndex = this.getAttribute('data-detail-index');
                    const card = cardsData.find(card => card.elementId === cardId);
                    const detailInfo = card.detailBoxes[detailIndex];
                    showNotification(detailInfo.title, detailInfo.fullDetails || detailInfo.content);
                });
            });
        });

        // Center last row of cards
        const cards = document.querySelectorAll('.card');
        const containerWidth = cardsContainer.offsetWidth;
        const cardWidth = cards[0].offsetWidth;
        const cardsPerRow = Math.floor(containerWidth / cardWidth);
        const lastRowStart = Math.floor(cards.length / cardsPerRow) * cardsPerRow;

        for (let i = lastRowStart; i < cards.length; i++) {
            cards[i].style.marginLeft = 'auto';
            cards[i].style.marginRight = 'auto';
        }
    }

    // Function to show notifications
    window.showNotification = function(title, content) {
        const notificationOverlay = document.getElementById('notificationOverlay');
        const notificationTitle = document.getElementById('notificationTitle');
        const notificationBody = document.getElementById('notificationBody');

        notificationTitle.textContent = title;
        notificationBody.innerHTML = content;

        notificationOverlay.classList.add('active');
    }

    // Close notification when clicking the close button
    document.getElementById('notificationClose').addEventListener('click', function() {
        document.getElementById('notificationOverlay').classList.remove('active');
    });

    // Close notification when clicking outside the notification content
    document.getElementById('notificationOverlay').addEventListener('click', function(e) {
        if (e.target === this) {
            this.classList.remove('active');
        }
    });

    // Function to update letter spacing
    function updateLetterSpacing() {
        const heading = document.querySelector('.heading');
        const headingWidth = heading.offsetWidth;
        const spacing = headingWidth * 0.02; // 2% of heading width
        heading.style.letterSpacing = `${spacing}px`;
    }

    // Call updateLetterSpacing on load and resize
    window.addEventListener('load', updateLetterSpacing);
    window.addEventListener('resize', updateLetterSpacing);

    // Search functionality
    searchBar.addEventListener('input', function() {
        const searchTerm = this.value.toLowerCase();
        const suggestions = cardsData.filter(card => 
            card.title.toLowerCase().includes(searchTerm) || 
            card.subtitle.toLowerCase().includes(searchTerm)
        ).map(card => card.title);

        if (suggestions.length > 0 && searchTerm.length > 0) {
            searchSuggestions.innerHTML = suggestions.map(suggestion => 
                `<div class="suggestion-item">${suggestion}</div>`
            ).join('');
            searchSuggestions.style.display = 'block';
        } else {
            searchSuggestions.style.display = 'none';
        }

        const filteredCards = cardsData.filter(card => 
            card.title.toLowerCase().includes(searchTerm) || 
            card.subtitle.toLowerCase().includes(searchTerm)
        );
        currentFilter = 'all'; // Reset to 'all' when searching
        filterButtons.forEach(btn => btn.classList.remove('active'));
        document.querySelector('[data-filter="all"]').classList.add('active');
        renderCards(filteredCards);
    });

    // Handle suggestion clicks
    searchSuggestions.addEventListener('click', function(e) {
        if (e.target.classList.contains('suggestion-item')) {
            searchBar.value = e.target.textContent;
            searchSuggestions.style.display = 'none';
            const filteredCards = cardsData.filter(card => 
                card.title.toLowerCase().includes(searchBar.value.toLowerCase()) || 
                card.subtitle.toLowerCase().includes(searchBar.value.toLowerCase())
            );
            renderCards(filteredCards);
        }
    });

    // Hide suggestions when clicking outside
    document.addEventListener('click', function(e) {
        if (e.target !== searchBar && e.target !== searchSuggestions) {
            searchSuggestions.style.display = 'none';
        }
    });

    // Filter functionality
    filterButtons.forEach(button => {
        button.addEventListener('click', function() {
            filterButtons.forEach(btn => btn.classList.remove('active'));
            this.classList.add('active');
            currentFilter = this.getAttribute('data-filter');
            const filteredCards = currentFilter === 'all' ? cardsData : cardsData.filter(card => card.type === currentFilter);
            renderCards(filteredCards);
        });
    });

    // Function to add a pulsing effect to a card
    function addPulseEffect(cardId) {
        const card = document.getElementById(cardId);
        if (card) {
            card.classList.add('pulse');
            setTimeout(() => {
                card.classList.remove('pulse');
            }, 2000);
        }
    }

    // Example usage: Add pulse effect to Bitcoin card every 5 minutes
    setInterval(() => {
        addPulseEffect('bitcoin');
    }, 300000);

    // Function to copy contract code
    window.copyContractCode = function(cardId) {
        const codeElement = document.querySelector(`#${cardId} .contract-code pre code`);
        const tooltipElement = document.querySelector(`#${cardId} .copied-tooltip`);
        
        if (codeElement) {
            const textToCopy = codeElement.textContent;
            navigator.clipboard.writeText(textToCopy).then(() => {
                tooltipElement.classList.add('show');
                setTimeout(() => {
                    tooltipElement.classList.remove('show');
                }, 2000);
            });
        }
    }

    // Initial render
    renderCards();

    // Add resize event listener to adjust chart size
    window.addEventListener('resize', () => {
        cardsData.forEach(cardData => {
            if (cardData.type === 'crypto') {
                const chart = document.getElementById(`${cardData.elementId}-tv-chart-container`);
                if (chart) {
                    chart.style.width = '100%';
                    chart.style.height = '300px';
                }
            }
        });
    });
});
</script>
    <script type="text/javascript" src="https://s3.tradingview.com/tv.js"></script>
</body>
</html>

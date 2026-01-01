<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>加斯顿智能锁 - 安全便捷守护家门</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" crossorigin="anonymous" referrerpolicy="no-referrer">
    <style>
        /* 原有CSS保持不变 */
        :root {
            --primary-color: #3B82F6;
            --primary-dark: #2563EB;
            --text-main: #333;
            --text-secondary: #666;
            --text-light: #888;
            --bg-white: #fff;
            --bg-light: #f9f9f9;
            --bg-blue-light: #f5f9ff;
            --bg-dark: #1E293B;
            --shadow-sm: 0 2px 5px rgba(0,0,0,0.05);
            --shadow-md: 0 5px 15px rgba(0,0,0,0.08);
            --shadow-lg: 0 10px 30px rgba(0,0,0,0.12);
            --radius-sm: 4px;
            --radius-md: 6px;
            --radius-lg: 10px;
            --transition-normal: 0.3s cubic-bezier(0.25, 0.1, 0.25, 1);
            --transition-slow: 0.6s cubic-bezier(0.25, 0.1, 0.25, 1);
            --section-padding: 60px 0;
            --section-padding-mobile: 40px 0;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: "Microsoft YaHei", "PingFang SC", sans-serif;
        }

        body {
            color: var(--text-main);
            background-color: var(--bg-light);
            line-height: 1.6;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
            scroll-behavior: smooth;
        }

        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
        }

        a {
            text-decoration: none;
            color: var(--text-main);
        }

        .btn {
            display: inline-block;
            padding: 10px 20px;
            border-radius: var(--radius-md);
            font-weight: bold;
            cursor: pointer;
            transition: background-color var(--transition-normal), 
                        transform var(--transition-normal);
            transform: translateZ(0);
            border: none;
            text-align: center;
        }

        .btn-primary {
            background-color: var(--primary-color);
            color: white;
        }

        .btn-primary:hover {
            background-color: var(--primary-dark);
            transform: translateY(-2px) translateZ(0);
        }

        .btn-primary:disabled {
            background-color: #93C5FD;
            cursor: not-allowed;
            transform: none;
        }

        .btn-outline {
            background-color: transparent;
            color: var(--primary-color);
            border: 1px solid var(--primary-color);
        }

        .btn-outline:hover {
            background-color: #EFF6FF;
            transform: translateY(-2px) translateZ(0);
        }

        .section {
            padding: var(--section-padding);
            opacity: 0;
            transform: translateY(20px);
            transition: opacity var(--transition-slow), 
                        transform var(--transition-slow);
        }

        .section.active {
            opacity: 1;
            transform: translateY(0);
        }

        .section-title {
            text-align: center;
            font-size: 28px;
            margin-bottom: 20px;
            color: var(--bg-dark);
            position: relative;
        }

        .section-title::after {
            content: "";
            display: block;
            width: 60px;
            height: 3px;
            background-color: var(--primary-color);
            margin: 10px auto 0;
            border-radius: 2px;
        }

        .section-desc {
            text-align: center;
            color: var(--text-secondary);
            max-width: 800px;
            margin: 0 auto 40px;
            font-size: 15px;
        }

        .nav {
            background-color: var(--bg-white);
            padding: 15px 0;
            box-shadow: var(--shadow-sm);
            position: sticky;
            top: 0;
            z-index: 999;
            transition: background-color var(--transition-normal), 
                        padding var(--transition-normal);
        }

        .nav.scroll {
            padding: 10px 0;
            background-color: rgba(255, 255, 255, 0.98);
            box-shadow: var(--shadow-md);
        }

        .nav .container {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            display: flex;
            align-items: center;
            font-size: 22px;
            font-weight: bold;
            color: var(--bg-dark);
            transition: opacity var(--transition-normal);
        }

        .logo i {
            color: var(--primary-color);
            margin-right: 10px;
            font-size: 24px;
        }

        .nav-menu {
            display: flex;
            gap: 30px;
        }

        .nav-menu a {
            font-weight: 500;
            color: var(--text-secondary);
            transition: color var(--transition-normal);
            position: relative;
        }

        .nav-menu a::after {
            content: "";
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background-color: var(--primary-color);
            transition: width var(--transition-normal);
        }

        .nav-menu a:hover::after, .nav-menu a.active::after {
            width: 100%;
        }

        .nav-menu a:hover, .nav-menu a.active {
            color: var(--primary-color);
        }

        .nav-btns {
            display: flex;
            gap: 15px;
        }

        .mobile-menu-btn {
            display: none;
            font-size: 20px;
            color: var(--text-secondary);
            background: transparent;
            border: none;
            cursor: pointer;
            transition: color var(--transition-normal);
        }

        .mobile-menu-btn:hover {
            color: var(--primary-color);
        }

        .hero {
            background: linear-gradient(to bottom, var(--bg-blue-light), var(--bg-light));
            padding-top: 80px;
            opacity: 1;
            transform: translateY(0);
        }

        .hero .container {
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            gap: 40px;
        }

        .hero-text {
            flex: 1;
            min-width: 300px;
        }

        .hero-title {
            font-size: 36px;
            margin-bottom: 20px;
            color: var(--bg-dark);
            line-height: 1.3;
        }

        .hero-title span {
            color: var(--primary-color);
            position: relative;
        }

        .hero-title span::after {
            content: "";
            position: absolute;
            bottom: 5px;
            left: 0;
            width: 100%;
            height: 8px;
            background-color: rgba(59, 130, 246, 0.1);
            border-radius: 4px;
            z-index: -1;
        }

        .hero-desc {
            color: var(--text-secondary);
            margin-bottom: 30px;
            font-size: 16px;
            line-height: 1.7;
        }

        .hero-stats {
            display: flex;
            gap: 40px;
            margin-top: 40px;
            flex-wrap: wrap;
        }

        .stat-item {
            text-align: center;
            flex: 1;
            min-width: 80px;
            transition: transform var(--transition-normal);
        }

        .stat-item:hover {
            transform: scale(1.05) translateZ(0);
        }

        .stat-num {
            font-size: 24px;
            font-weight: bold;
            color: var(--primary-color);
            margin-bottom: 5px;
        }

        .stat-text {
            color: var(--text-secondary);
            font-size: 14px;
        }

        .hero-img {
            flex: 1;
            min-width: 300px;
            transition: transform var(--transition-normal);
        }

        .hero-img:hover {
            transform: scale(1.02) translateZ(0);
        }

        .hero-img img {
            width: 100%;
            height: auto;
            max-height: 600px;
            border-radius: var(--radius-lg);
            box-shadow: 0 5px 15px rgba(0,0,0,0.08);
            object-fit: cover;
        }

        .products {
            background-color: var(--bg-white);
        }

        .product-list {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .product-card {
            background-color: var(--bg-light);
            border-radius: var(--radius-lg);
            overflow: hidden;
            box-shadow: var(--shadow-sm);
            transition: transform var(--transition-normal), 
                        box-shadow var(--transition-normal);
            transform: translateZ(0);
        }

        .product-card:hover {
            transform: translateY(-5px) translateZ(0);
            box-shadow: var(--shadow-lg);
        }

        .product-img {
            position: relative;
            overflow: hidden;
            height: 200px;
        }

        .product-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform var(--transition-normal);
        }

        .product-card:hover .product-img img {
            transform: scale(1.05);
        }

        .product-tag {
            position: absolute;
            top: 15px;
            right: 15px;
            background-color: var(--primary-color);
            color: white;
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: bold;
        }

        .product-stats {
            position: absolute;
            bottom: 15px;
            left: 15px;
            display: flex;
            gap: 15px;
            font-size: 12px;
            color: white;
            text-shadow: 0 1px 2px rgba(0,0,0,0.3);
        }

        .product-info {
            padding: 20px;
        }

        .product-name {
            font-size: 20px;
            margin-bottom: 10px;
            color: var(--bg-dark);
            font-weight: 600;
        }

        .product-desc {
            color: var(--text-secondary);
            margin-bottom: 15px;
            font-size: 14px;
            line-height: 1.6;
        }

        .product-params {
            font-size: 13px;
            color: var(--text-light);
            margin-bottom: 15px;
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
        }

        .product-params span {
            background-color: #f1f5f9;
            padding: 3px 8px;
            border-radius: var(--radius-sm);
        }

        .product-price {
            font-size: 18px;
            font-weight: bold;
            color: var(--primary-color);
            margin-bottom: 15px;
        }

        .product-btns {
            display: flex;
            gap: 10px;
        }

        .product-btns .btn {
            flex: 1;
            padding: 8px 0;
            font-size: 14px;
        }

        .features {
            background-color: var(--bg-blue-light);
        }

        .feature-list {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
        }

        .feature-item {
            background-color: var(--bg-white);
            padding: 25px;
            border-radius: var(--radius-lg);
            text-align: center;
            box-shadow: var(--shadow-sm);
            transition: background-color var(--transition-normal), 
                        transform var(--transition-normal);
            transform: translateZ(0);
        }

        .feature-item:hover {
            background-color: #EFF6FF;
            transform: translateY(-3px) translateZ(0);
        }

        .feature-item i {
            font-size: 28px;
            color: var(--primary-color);
            margin-bottom: 15px;
            transition: transform var(--transition-normal);
        }

        .feature-item:hover i {
            transform: rotate(5deg) scale(1.1);
        }

        .feature-name {
            font-weight: bold;
            margin-bottom: 10px;
            color: var(--bg-dark);
            font-size: 16px;
        }

        .feature-desc {
            font-size: 14px;
            color: var(--text-secondary);
            line-height: 1.6;
        }

        .app-download {
            background-color: var(--bg-white);
            padding: 80px 0;
        }

        .app-wrap {
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            gap: 50px;
            justify-content: center;
        }

        .app-img {
            flex: 1;
            min-width: 250px;
            text-align: center;
        }

        .app-img img {
            width: 200px;
            height: auto;
            border-radius: 30px;
            box-shadow: 0 10px 30px rgba(59, 130, 246, 0.2);
            transition: transform var(--transition-normal);
        }

        .app-img img:hover {
            transform: translateY(-10px) scale(1.05) translateZ(0);
        }

        .app-qrcode {
            margin-top: 20px;
            text-align: center;
        }

        .app-qrcode img {
            width: 120px;
            height: 120px;
            border-radius: var(--radius-md);
            border: 2px solid #f1f1f1;
        }

        .app-qrcode p {
            font-size: 13px;
            color: var(--text-secondary);
            margin-top: 10px;
        }

        .app-info {
            flex: 1;
            min-width: 300px;
        }

        .app-title {
            font-size: 26px;
            color: var(--bg-dark);
            margin-bottom: 15px;
        }

        .app-title span {
            color: var(--primary-color);
        }

        .app-desc {
            color: var(--text-secondary);
            margin-bottom: 20px;
            line-height: 1.7;
        }

        .app-features {
            margin-bottom: 30px;
        }

        .app-feature-item {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 10px;
            color: var(--text-secondary);
        }

        .app-feature-item i {
            color: var(--primary-color);
            font-size: 16px;
        }

        .download-btns {
            display: flex;
            gap: 20px;
            flex-wrap: wrap;
        }

        .download-btn {
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 12px 25px;
            border-radius: 8px;
            color: white;
            transition: transform var(--transition-normal), 
                        opacity var(--transition-normal);
        }

        .download-btn.ios {
            background-color: #000;
        }

        .download-btn.android {
            background-color: #3DDC84;
        }

        .download-btn:hover {
            transform: translateY(-3px) translateZ(0);
            opacity: 0.95;
        }

        .download-btn i {
            font-size: 20px;
        }

        .download-text {
            text-align: left;
        }

        .download-text .small {
            font-size: 12px;
            opacity: 0.8;
        }

        .download-text .big {
            font-size: 14px;
            font-weight: bold;
        }

        .contact {
            background-color: var(--bg-light);
        }

        .contact .container {
            display: flex;
            flex-wrap: wrap;
            gap: 40px;
        }

        .contact-info {
            flex: 1;
            min-width: 300px;
        }

        .contact-item {
            display: flex;
            align-items: flex-start;
            gap: 15px;
            margin-bottom: 25px;
            transition: transform var(--transition-normal);
        }

        .contact-item:hover {
            transform: translateX(5px);
        }

        .contact-item i {
            font-size: 20px;
            color: var(--primary-color);
            margin-top: 5px;
            width: 24px;
            text-align: center;
        }

        .contact-title {
            font-weight: bold;
            margin-bottom: 5px;
            color: var(--bg-dark);
            font-size: 16px;
        }

        .contact-text {
            color: var(--text-secondary);
            line-height: 1.6;
        }

        .contact-form {
            flex: 1;
            min-width: 300px;
            background-color: var(--bg-white);
            padding: 30px;
            border-radius: var(--radius-lg);
            box-shadow: var(--shadow-sm);
            transition: box-shadow var(--transition-normal);
        }

        .contact-form:hover {
            box-shadow: var(--shadow-md);
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            color: var(--text-secondary);
            font-weight: 500;
        }

        .form-group input, .form-group select, .form-group textarea {
            width: 100%;
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: var(--radius-md);
            font-size: 14px;
            color: var(--text-main);
            transition: border-color var(--transition-normal), 
                        box-shadow var(--transition-normal);
        }

        .form-group input:focus, .form-group select:focus, .form-group textarea:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
        }

        .form-group textarea {
            height: 120px;
            resize: none;
        }

        .form-tip {
            font-size: 12px;
            color: #ef4444;
            margin-top: 5px;
            display: none;
        }

        .form-tip.active {
            display: block;
        }

        .footer {
            background-color: var(--bg-dark);
            color: #ccc;
            padding: 50px 0 20px;
        }

        .footer .container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 30px;
            margin-bottom: 30px;
        }

        .footer-logo {
            font-size: 22px;
            font-weight: bold;
            color: white;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
        }

        .footer-logo i {
            color: var(--primary-color);
            margin-right: 10px;
        }

        .footer-desc {
            font-size: 14px;
            line-height: 1.7;
            margin-bottom: 15px;
        }

        .footer-social a {
            color: #ccc;
            font-size: 18px;
            margin-right: 15px;
            transition: color var(--transition-normal), 
                        transform var(--transition-normal);
        }

        .footer-social a:hover {
            color: var(--primary-color);
            transform: translateY(-3px) rotate(5deg);
        }

        .footer-title {
            font-size: 18px;
            color: white;
            margin-bottom: 15px;
            font-weight: bold;
        }

        .footer-links li {
            list-style: none;
            margin-bottom: 10px;
        }

        .footer-links a {
            color: #ccc;
            font-size: 14px;
            transition: color var(--transition-normal), 
                        padding-left var(--transition-normal);
        }

        .footer-links a:hover {
            color: var(--primary-color);
            padding-left: 5px;
        }

        .copyright {
            text-align: center;
            font-size: 12px;
            padding-top: 20px;
            border-top: 1px solid #333;
            color: #888;
        }

        .login-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            opacity: 0;
            visibility: hidden;
            transition: opacity var(--transition-normal), 
                        visibility var(--transition-normal);
        }

        .login-modal.active {
            opacity: 1;
            visibility: visible;
        }

        .login-box {
            background-color: var(--bg-white);
            width: 90%;
            max-width: 400px;
            border-radius: var(--radius-lg);
            padding: 30px;
            box-shadow: var(--shadow-lg);
            transform: translateY(-20px) scale(0.95);
            transition: transform var(--transition-normal);
        }

        .login-modal.active .login-box {
            transform: translateY(0) scale(1);
        }

        .login-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
        }

        .login-title {
            font-size: 20px;
            font-weight: bold;
            color: var(--bg-dark);
        }

        .close-login {
            background: transparent;
            border: none;
            font-size: 20px;
            color: var(--text-secondary);
            cursor: pointer;
            transition: color var(--transition-normal), 
                        transform var(--transition-normal);
        }

        .close-login:hover {
            color: #ef4444;
            transform: rotate(90deg);
        }

        .login-form .form-group {
            margin-bottom: 18px;
        }

        .pwd-group {
            position: relative;
        }

        .toggle-pwd {
            position: absolute;
            right: 12px;
            top: 38px;
            color: var(--text-secondary);
            cursor: pointer;
            transition: color var(--transition-normal);
        }

        .toggle-pwd:hover {
            color: var(--primary-color);
        }

        .remember-group {
            display: flex;
            align-items: center;
            gap: 8px;
            margin-bottom: 20px;
            font-size: 14px;
            color: var(--text-secondary);
        }

        .remember-group input {
            width: 16px;
            height: 16px;
            accent-color: var(--primary-color);
        }

        .login-links {
            display: flex;
            justify-content: space-between;
            font-size: 13px;
            margin-top: 15px;
        }

        .login-links a {
            color: var(--primary-color);
            transition: color var(--transition-normal);
        }

        .login-links a:hover {
            color: var(--primary-dark);
            text-decoration: underline;
        }

        .product-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            opacity: 0;
            visibility: hidden;
            transition: opacity var(--transition-normal), 
                        visibility var(--transition-normal);
            padding: 20px 0;
            overflow-y: auto;
        }

        .product-modal.active {
            opacity: 1;
            visibility: visible;
        }

        .product-detail-box {
            background-color: var(--bg-white);
            width: 90%;
            max-width: 800px;
            border-radius: var(--radius-lg);
            padding: 30px;
            box-shadow: var(--shadow-lg);
            transform: translateY(-20px) scale(0.95);
            transition: transform var(--transition-normal);
        }

        .product-modal.active .product-detail-box {
            transform: translateY(0) scale(1);
        }

        .product-detail-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
            padding-bottom: 15px;
            border-bottom: 1px solid #f1f1f1;
        }

        .product-detail-title {
            font-size: 22px;
            font-weight: bold;
            color: var(--bg-dark);
        }

        .close-product {
            background: transparent;
            border: none;
            font-size: 20px;
            color: var(--text-secondary);
            cursor: pointer;
            transition: color var(--transition-normal);
        }

        .close-product:hover {
            color: #ef4444;
        }

        .product-detail-content {
            display: flex;
            flex-wrap: wrap;
            gap: 30px;
        }

        .product-detail-img {
            flex: 1;
            min-width: 300px;
        }

        .product-detail-img img {
            width: 100%;
            height: auto;
            border-radius: var(--radius-md);
            box-shadow: var(--shadow-sm);
        }

        .product-detail-info {
            flex: 1;
            min-width: 300px;
        }

        .product-detail-price {
            font-size: 24px;
            font-weight: bold;
            color: var(--primary-color);
            margin-bottom: 15px;
        }

        .product-detail-tag {
            display: inline-block;
            background-color: #EFF6FF;
            color: var(--primary-color);
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 12px;
            margin-bottom: 20px;
        }

        .product-detail-desc {
            color: var(--text-secondary);
            margin-bottom: 20px;
            line-height: 1.7;
        }

        .product-detail-params {
            margin-bottom: 25px;
        }

        .product-detail-params h4 {
            font-size: 16px;
            color: var(--bg-dark);
            margin-bottom: 10px;
        }

        .product-detail-params table {
            width: 100%;
            border-collapse: collapse;
            font-size: 14px;
        }

        .product-detail-params td {
            padding: 8px 0;
            border-bottom: 1px solid #f1f1f1;
        }

        .product-detail-params td:first-child {
            color: var(--text-light);
            width: 30%;
        }

        .product-detail-params td:last-child {
            color: var(--text-main);
        }

        .mobile-menu-mask {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.3);
            z-index: 9997;
            opacity: 0;
            visibility: hidden;
            transition: opacity var(--transition-normal);
        }

        .mobile-menu-mask.active {
            opacity: 1;
            visibility: visible;
        }

        .mobile-menu {
            position: fixed;
            top: 0;
            right: 0;
            width: 80%;
            max-width: 300px;
            height: 100%;
            background-color: var(--bg-white);
            padding: 20px;
            box-shadow: -2px 0 10px rgba(0,0,0,0.1);
            transform: translateX(100%);
            transition: transform var(--transition-normal);
            z-index: 9998;
            padding-top: 80px;
        }

        .mobile-menu.active {
            transform: translateX(0);
        }

        .mobile-menu-list {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .mobile-menu-list a {
            font-size: 16px;
            color: var(--text-secondary);
            font-weight: 500;
            padding: 10px 0;
            border-bottom: 1px solid #f1f1f1;
            transition: color var(--transition-normal);
        }

        .mobile-menu-list a:hover, .mobile-menu-list a.active {
            color: var(--primary-color);
        }

        .mobile-menu-btns {
            display: flex;
            flex-direction: column;
            gap: 15px;
            margin-top: 30px;
        }

        .close-mobile-menu {
            position: absolute;
            top: 20px;
            right: 20px;
            font-size: 20px;
            color: var(--text-secondary);
            background: transparent;
            border: none;
            cursor: pointer;
        }

        .back-to-top {
            position: fixed;
            bottom: 30px;
            right: 30px;
            width: 45px;
            height: 45px;
            background-color: var(--primary-color);
            color: white;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 20px;
            box-shadow: var(--shadow-md);
            cursor: pointer;
            opacity: 0;
            visibility: hidden;
            transition: opacity var(--transition-normal), 
                        transform var(--transition-normal);
            z-index: 999;
        }

        .back-to-top.active {
            opacity: 1;
            visibility: visible;
            transform: translateY(0);
        }

        .back-to-top:hover {
            background-color: var(--primary-dark);
            transform: translateY(-3px);
        }

        @media (max-width: 768px) {
            :root {
                --section-padding: var(--section-padding-mobile);
            }

            .nav-menu, .nav-btns {
                display: none;
            }

            .mobile-menu-btn {
                display: block;
            }

            .hero-title {
                font-size: 28px;
            }

            .hero-stats {
                gap: 20px;
            }

            .app-download {
                padding: 50px 0;
            }

            .app-wrap {
                gap: 30px;
            }

            .download-btns {
                gap: 15px;
            }

            .download-btn {
                padding: 10px 20px;
            }

            .product-detail-content {
                gap: 20px;
            }

            .back-to-top {
                width: 40px;
                height: 40px;
                bottom: 20px;
                right: 20px;
                font-size: 18px;
            }
        }
    </style>
</head>
<body>
    <!-- 导航栏 -->
    <nav class="nav" id="mainNav">
        <div class="container">
            <a href="#" class="logo">
                <i class="fa-solid fa-lock"></i>
                <span>加斯顿智能锁</span>
            </a>
            <div class="nav-menu">
                <a href="#hero" class="active">首页</a>
                <a href="#products">产品中心</a>
                <a href="#features">核心功能</a>
                <a href="#app-download">APP下载</a>
                <a href="#contact">联系我们</a>
            </div>
            <div class="nav-btns">
                <button class="btn btn-outline" id="registerBtn">注册</button>
                <button class="btn btn-primary" id="loginBtn">登录</button>
            </div>
            <button class="mobile-menu-btn" id="mobileMenuBtn">
                <i class="fa-solid fa-bars"></i>
            </button>
        </div>
    </nav>

    <!-- 移动端菜单 -->
    <div class="mobile-menu-mask" id="mobileMenuMask"></div>
    <div class="mobile-menu" id="mobileMenu">
        <button class="close-mobile-menu" id="closeMobileMenu">
            <i class="fa-solid fa-xmark"></i>
        </button>
        <div class="mobile-menu-list">
            <a href="#hero" class="mobile-link">首页</a>
            <a href="#products" class="mobile-link">产品中心</a>
            <a href="#features" class="mobile-link">核心功能</a>
            <a href="#app-download" class="mobile-link">APP下载</a>
            <a href="#contact" class="mobile-link">联系我们</a>
        </div>
        <div class="mobile-menu-btns">
            <button class="btn btn-outline" id="mobileRegisterBtn">注册</button>
            <button class="btn btn-primary" id="mobileLoginBtn">登录</button>
        </div>
    </div>

    <!-- 英雄区 -->
    <section class="hero section" id="hero">
        <div class="container">
            <div class="hero-text">
                <h1 class="hero-title">
                    智能锁，<br>让<span>家门更安全</span>，让生活更便捷
                </h1>
                <p class="hero-desc">
                    加斯顿智能锁采用先进生物识别技术，支持指纹、密码、手机等多种解锁方式，
                    为您的家庭安全保驾护航，告别钥匙烦恼，开启智能生活新体验。
                </p>
                <div>
                    <button class="btn btn-primary">立即购买</button>
                    <button class="btn btn-outline">了解更多</button>
                </div>
                <div class="hero-stats">
                    <div class="stat-item">
                        <div class="stat-num">100万+</div>
                        <div class="stat-text">用户选择</div>
                    </div>
                    <div class="stat-item">
                        <div class="stat-num">5秒</div>
                        <div class="stat-text">快速识别</div>
                    </div>
                    <div class="stat-item">
                        <div class="stat-num">99.9%</div>
                        <div class="stat-text">识别准确率</div>
                    </div>
                    <div class="stat-item">
                        <div class="stat-num">365天</div>
                        <div class="stat-text">超长续航</div>
                    </div>
                </div>
            </div>
            <div class="hero-img">
                <img src="https://picsum.photos/id/1/600/600" alt="加斯顿智能锁">
            </div>
        </div>
    </section>

    <!-- 产品中心 -->
    <section class="products section" id="products">
        <div class="container">
            <h2 class="section-title">产品中心</h2>
            <p class="section-desc">
                我们提供多种型号的智能锁产品，满足不同家庭的需求，无论是传统门还是智能门，
                都能找到适合的解决方案。
            </p>
            <div class="product-list" id="productList">
                <!-- 产品1 -->
                <div class="product-card">
                    <div class="product-img">
                        <img src="https://picsum.photos/id/20/600/400" alt="智能锁A1">
                        <span class="product-tag">热销</span>
                        <div class="product-stats">
                            <span><i class="fa-solid fa-shield"></i> C级锁芯</span>
                            <span><i class="fa-solid fa-battery-full"></i> 365天续航</span>
                        </div>
                    </div>
                    <div class="product-info">
                        <h3 class="product-name">加斯顿A1智能锁</h3>
                        <p class="product-desc">全自动指纹锁，支持指纹、密码、刷卡、手机APP等多种解锁方式，适合多种门型</p>
                        <div class="product-params">
                            <span>指纹解锁</span>
                            <span>密码解锁</span>
                            <span>APP控制</span>
                        </div>
                        <div class="product-price">¥1299</div>
                        <div class="product-btns">
                            <button class="btn btn-outline view-product" data-id="1">查看详情</button>
                            <button class="btn btn-primary">立即购买</button>
                        </div>
                    </div>
                </div>

                <!-- 产品2 -->
                <div class="product-card">
                    <div class="product-img">
                        <img src="https://picsum.photos/id/21/600/400" alt="智能锁B2">
                        <span class="product-tag">新品</span>
                        <div class="product-stats">
                            <span><i class="fa-solid fa-shield"></i> C级锁芯</span>
                            <span><i class="fa-solid fa-battery-full"></i> 500天续航</span>
                        </div>
                    </div>
                    <div class="product-info">
                        <h3 class="product-name">加斯顿B2人脸识别锁</h3>
                        <p class="product-desc">3D结构光人脸识别，全自动开锁，支持多种解锁方式，适合高端家庭使用</p>
                        <div class="product-params">
                            <span>人脸识别</span>
                            <span>指纹解锁</span>
                            <span>远程控制</span>
                        </div>
                        <div class="product-price">¥2599</div>
                        <div class="product-btns">
                            <button class="btn btn-outline view-product" data-id="2">查看详情</button>
                            <button class="btn btn-primary">立即购买</button>
                        </div>
                    </div>
                </div>

                <!-- 产品3 -->
                <div class="product-card">
                    <div class="product-img">
                        <img src="https://picsum.photos/id/22/600/400" alt="智能锁C3">
                        <span class="product-tag">经济款</span>
                        <div class="product-stats">
                            <span><i class="fa-solid fa-shield"></i> C级锁芯</span>
                            <span><i class="fa-solid fa-battery-full"></i> 200天续航</span>
                        </div>
                    </div>
                    <div class="product-info">
                        <h3 class="product-name">加斯顿C3基础款智能锁</h3>
                        <p class="product-desc">高性价比智能锁，支持指纹、密码、钥匙三种基础解锁方式，安装简单</p>
                        <div class="product-params">
                            <span>指纹解锁</span>
                            <span>密码解锁</span>
                            <span>钥匙解锁</span>
                        </div>
                        <div class="product-price">¥899</div>
                        <div class="product-btns">
                            <button class="btn btn-outline view-product" data-id="3">查看详情</button>
                            <button class="btn btn-primary">立即购买</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- 核心功能 -->
    <section class="features section" id="features">
        <div class="container">
            <h2 class="section-title">核心功能</h2>
            <p class="section-desc">
                加斯顿智能锁集成多项先进技术，为您带来安全、便捷的使用体验，
                让每一次开门都充满科技感。
            </p>
            <div class="feature-list">
                <div class="feature-item">
                    <i class="fa-solid fa-fingerprint"></i>
                    <h3 class="feature-name">指纹识别</h3>
                    <p class="feature-desc">采用半导体指纹头，识别速度快，准确率高，支持干湿手指识别</p>
                </div>
                <div class="feature-item">
                    <i class="fa-solid fa-mobile-screen-button"></i>
                    <h3 class="feature-name">手机控制</h3>
                    <p class="feature-desc">通过APP远程控制门锁，支持远程开锁、查看开锁记录、发送临时密码</p>
                </div>
                <div class="feature-item">
                    <i class="fa-solid fa-shield-halved"></i>
                    <h3 class="feature-name">多重防护</h3>
                    <p class="feature-desc">C级锁芯，防小黑盒破解，防撬报警，异常尝试报警，保障家庭安全</p>
                </div>
                <div class="feature-item">
                    <i class="fa-solid fa-bell"></i>
                    <h3 class="feature-name">实时报警</h3>
                    <p class="feature-desc">异常情况实时推送至手机，包括撬锁、试错、低电量等状态提醒</p>
                </div>
                <div class="feature-item">
                    <i class="fa-solid fa-key"></i>
                    <h3 class="feature-name">多种解锁</h3>
                    <p class="feature-desc">支持指纹、密码、刷卡、手机、钥匙等多种解锁方式，满足不同场景</p>
                </div>
                <div class="feature-item">
                    <i class="fa-solid fa-battery-full"></i>
                    <h3 class="feature-name">超长续航</h3>
                    <p class="feature-desc">低功耗设计，4节AA电池可支持正常使用12个月以上，电量低时提醒</p>
                </div>
            </div>
        </div>
    </section>

    <!-- APP下载 -->
    <section class="app-download section" id="app-download">
        <div class="container">
            <div class="app-wrap">
                <div class="app-img">
                    <img src="https://picsum.photos/id/119/300/600" alt="加斯顿APP">
                    <div class="app-qrcode">
                        <img src="https://picsum.photos/id/237/200/200" alt="APP下载二维码">
                        <p>扫码下载APP</p>
                    </div>
                </div>
                <div class="app-info">
                    <h2 class="app-title">
                        下载<span>加斯顿APP</span>，掌控智能生活
                    </h2>
                    <p class="app-desc">
                        通过加斯顿APP，您可以远程控制智能锁，查看开门记录，设置临时密码，
                        接收异常报警等，让您随时随地掌握家门动态，为家庭安全增添一份保障。
                    </p>
                    <div class="app-features">
                        <div class="app-feature-item">
                            <i class="fa-solid fa-check-circle"></i>
                            <span>远程查看开门记录，了解家人出入情况</span>
                        </div>
                        <div class="app-feature-item">
                            <i class="fa-solid fa-check-circle"></i>
                            <span>生成临时密码，方便访客临时进入</span>
                        </div>
                        <div class="app-feature-item">
                            <i class="fa-solid fa-check-circle"></i>
                            <span>实时接收报警信息，异常情况及时处理</span>
                        </div>
                        <div class="app-feature-item">
                            <i class="fa-solid fa-check-circle"></i>
                            <span>管理多个智能锁设备，一键操作便捷高效</span>
                        </div>
                    </div>
                    <div class="download-btns">
                        <a href="#" class="download-btn ios">
                            <i class="fa-brands fa-apple"></i>
                            <div class="download-text">
                                <div class="small">下载</div>
                                <div class="big">App Store</div>
                            </div>
                        </a>
                        <a href="#" class="download-btn android">
                            <i class="fa-brands fa-android"></i>
                            <div class="download-text">
                                <div class="small">下载</div>
                                <div class="big">Google Play</div>
                            </div>
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- 联系我们 -->
    <section class="contact section" id="contact">
        <div class="container">
            <h2 class="section-title">联系我们</h2>
            <p class="section-desc">
                如有任何疑问或需求，欢迎通过以下方式联系我们，我们将竭诚为您服务
            </p>
            <div class="contact-info">
                <div class="contact-item">
                    <i class="fa-solid fa-map-marker-alt"></i>
                    <div>
                        <h3 class="contact-title">公司地址</h3>
                        <p class="contact-text">北京市朝阳区科技园区88号加斯顿大厦15层</p>
                    </div>
                </div>
                <div class="contact-item">
                    <i class="fa-solid fa-phone"></i>
                    <div>
                        <h3 class="contact-title">联系电话</h3>
                        <p class="contact-text">400-888-9999</p>
                        <p class="contact-text">工作时间：周一至周日 9:00-21:00</p>
                    </div>
                </div>
                <div class="contact-item">
                    <i class="fa-solid fa-envelope"></i>
                    <div>
                        <h3 class="contact-title">电子邮箱</h3>
                        <p class="contact-text">service@gaston-lock.com</p>
                        <p class="contact-text">support@gaston-lock.com</p>
                    </div>
                </div>
                <div class="contact-item">
                    <i class="fa-solid fa-headphones"></i>
                    <div>
                        <h3 class="contact-title">售后服务</h3>
                        <p class="contact-text">提供3年免费质保，终身维护服务</p>
                        <p class="contact-text">专业安装团队，全国覆盖</p>
                    </div>
                </div>
            </div>
            <div class="contact-form">
                <form id="contactForm">
                    <div class="form-group">
                        <label for="name">姓名</label>
                        <input type="text" id="name" placeholder="请输入您的姓名">
                        <div class="form-tip">请输入姓名</div>
                    </div>
                    <div class="form-group">
                        <label for="phone">电话</label>
                        <input type="tel" id="phone" placeholder="请输入您的手机号码">
                        <div class="form-tip">请输入正确的手机号码</div>
                    </div>
                    <div class="form-group">
                        <label for="product">感兴趣的产品</label>
                        <select id="product">
                            <option value="">请选择产品</option>
                            <option value="A1">加斯顿A1智能锁</option>
                            <option value="B2">加斯顿B2人脸识别锁</option>
                            <option value="C3">加斯顿C3基础款智能锁</option>
                            <option value="other">其他产品</option>
                        </select>
                        <div class="form-tip">请选择产品</div>
                    </div>
                    <div class="form-group">
                        <label for="message">留言内容</label>
                        <textarea id="message" placeholder="请输入您的需求或疑问"></textarea>
                        <div class="form-tip">请输入留言内容</div>
                    </div>
                    <button type="submit" class="btn btn-primary" style="width: 100%;">提交留言</button>
                </form>
            </div>
        </div>
    </section>

    <!-- 页脚 -->
    <footer class="footer">
        <div class="container">
            <div class="footer-col">
                <div class="footer-logo">
                    <i class="fa-solid fa-lock"></i>
                    <span>加斯顿智能锁</span>
                </div>
                <p class="footer-desc">
                    加斯顿智能锁，致力于为全球家庭提供安全、便捷的智能门锁解决方案，
                    用科技守护每一个家庭的安全。
                </p>
                <div class="footer-social">
                    <a href="#"><i class="fa-brands fa-weixin"></i></a>
                    <a href="#"><i class="fa-brands fa-weibo"></i></a>
                    <a href="#"><i class="fa-brands fa-qq"></i></a>
                    <a href="#"><i class="fa-brands fa-youtube"></i></a>
                </div>
            </div>
            <div class="footer-col">
                <h3 class="footer-title">产品系列</h3>
                <ul class="footer-links">
                    <li><a href="#">A系列智能锁</a></li>
                    <li><a href="#">B系列人脸识别锁</a></li>
                    <li><a href="#">C系列基础款</a></li>
                    <li><a href="#">商用智能锁</a></li>
                    <li><a href="#">智能门控系统</a></li>
                </ul>
            </div>
            <div class="footer-col">
                <h3 class="footer-title">关于我们</h3>
                <ul class="footer-links">
                    <li><a href="#">公司简介</a></li>
                    <li><a href="#">发展历程</a></li>
                    <li><a href="#">新闻中心</a></li>
                    <li><a href="#">加入我们</a></li>
                    <li><a href="#">联系我们</a></li>
                </ul>
            </div>
            <div class="footer-col">
                <h3 class="footer-title">售后服务</h3>
                <ul class="footer-links">
                    <li><a href="#">安装指南</a></li>
                    <li><a href="#">使用手册</a></li>
                    <li><a href="#">常见问题</a></li>
                    <li><a href="#">保修政策</a></li>
                    <li><a href="#">预约维修</a></li>
                </ul>
            </div>
        </div>
        <div class="copyright">
            <p>© 2023 加斯顿智能科技有限公司 版权所有 京ICP备12345678号</p>
        </div>
    </footer>

    <!-- 登录模态框 -->
    <div class="login-modal" id="loginModal">
        <div class="login-box">
            <div class="login-header">
                <h3 class="login-title">用户登录</h3>
                <button class="close-login" id="closeLogin">
                    <i class="fa-solid fa-xmark"></i>
                </button>
            </div>
            <form class="login-form" id="loginForm">
                <div class="form-group">
                    <label for="loginPhone">手机号码</label>
                    <input type="tel" id="loginPhone" placeholder="请输入手机号码">
                    <div class="form-tip">请输入正确的手机号码</div>
                </div>
                <div class="form-group pwd-group">
                    <label for="loginPwd">密码</label>
                    <input type="password" id="loginPwd" placeholder="请输入密码">
                    <i class="fa-solid fa-eye toggle-pwd" id="togglePwd"></i>
                    <div class="form-tip">密码长度不少于6位</div>
                </div>
                <div class="remember-group">
                    <input type="checkbox" id="rememberPwd">
                    <label for="rememberPwd">记住密码</label>
                </div>
                <button type="submit" class="btn btn-primary" style="width: 100%;">登录</button>
                <div class="login-links">
                    <a href="#">忘记密码？</a>
                    <a href="#">还没有账号？注册</a>
                </div>
            </form>
        </div>
    </div>

    <!-- 产品详情模态框 -->
    <div class="product-modal" id="productModal">
        <div class="product-detail-box">
            <div class="product-detail-header">
                <h3 class="product-detail-title" id="modalProductTitle">产品详情</h3>
                <button class="close-product" id="closeProduct">
                    <i class="fa-solid fa-xmark"></i>
                </button>
            </div>
            <div class="product-detail-content" id="modalProductContent">
                <!-- 产品详情内容将通过JS动态填充 -->
            </div>
        </div>
    </div>

    <!-- 返回顶部按钮 -->
    <div class="back-to-top" id="backToTop">
        <i class="fa-solid fa-arrow-up"></i>
    </div>

    <script>
        // 页面加载完成后执行
        document.addEventListener('DOMContentLoaded', function() {
            // 导航栏滚动效果
            const nav = document.getElementById('mainNav');
            window.addEventListener('scroll', function() {
                if (window.scrollY > 50) {
                    nav.classList.add('scroll');
                } else {
                    nav.classList.remove('scroll');
                }
            });

            // 移动端菜单控制
            const mobileMenuBtn = document.getElementById('mobileMenuBtn');
            const closeMobileMenu = document.getElementById('closeMobileMenu');
            const mobileMenuMask = document.getElementById('mobileMenuMask');
            const mobileMenu = document.getElementById('mobileMenu');
            const mobileLinks = document.querySelectorAll('.mobile-link');

            mobileMenuBtn.addEventListener('click', function() {
                mobileMenu.classList.add('active');
                mobileMenuMask.classList.add('active');
                document.body.style.overflow = 'hidden';
            });

            function closeMenu() {
                mobileMenu.classList.remove('active');
                mobileMenuMask.classList.remove('active');
                document.body.style.overflow = '';
            }

            closeMobileMenu.addEventListener('click', closeMenu);
            mobileMenuMask.addEventListener('click', closeMenu);
            mobileLinks.forEach(link => {
                link.addEventListener('click', closeMenu);
            });

            // 登录模态框控制
            const loginBtn = document.getElementById('loginBtn');
            const mobileLoginBtn = document.getElementById('mobileLoginBtn');
            const loginModal = document.getElementById('loginModal');
            const closeLogin = document.getElementById('closeLogin');

            function openLoginModal() {
                loginModal.classList.add('active');
                document.body.style.overflow = 'hidden';
            }

            function closeLoginModal() {
                loginModal.classList.remove('active');
                document.body.style.overflow = '';
            }

            loginBtn.addEventListener('click', openLoginModal);
            mobileLoginBtn.addEventListener('click', openLoginModal);
            closeLogin.addEventListener('click', closeLoginModal);
            loginModal.addEventListener('click', function(e) {
                if (e.target === loginModal) {
                    closeLoginModal();
                }
            });

            // 密码显示/隐藏切换
            const togglePwd = document.getElementById('togglePwd');
            const loginPwd = document.getElementById('loginPwd');

            togglePwd.addEventListener('click', function() {
                const type = loginPwd.getAttribute('type') === 'password' ? 'text' : 'password';
                loginPwd.setAttribute('type', type);
                this.classList.toggle('fa-eye');
                this.classList.toggle('fa-eye-slash');
            });

            // 产品详情模态框控制
            const productModal = document.getElementById('productModal');
            const closeProduct = document.getElementById('closeProduct');
            const viewProductBtns = document.querySelectorAll('.view-product');
            const modalProductTitle = document.getElementById('modalProductTitle');
            const modalProductContent = document.getElementById('modalProductContent');

            // 产品数据
            const products = {
                1: {
                    name: "加斯顿A1智能锁",
                    price: "¥1299",
                    tag: "热销产品",
                    img: "https://picsum.photos/id/20/800/600",
                    desc: "加斯顿A1智能锁是一款高性价比的全自动智能锁，采用先进的指纹识别技术，识别速度快至0.3秒，准确率达99.9%。支持指纹、密码、刷卡、手机APP、应急钥匙等多种解锁方式，满足不同场景需求。",
                    params: {
                        "产品材质": "锌合金面板",
                        "指纹容量": "100枚",
                        "密码容量": "50组",
                        "卡片容量": "50张",
                        "工作电压": "6V（4节AA电池）",
                        "待机电流": "<50μA",
                        "工作温度": "-20℃~60℃",
                        "适用门厚": "40mm~120mm",
                        "开锁方式": "指纹、密码、刷卡、APP、钥匙"
                    }
                },
                2: {
                    name: "加斯顿B2人脸识别锁",
                    price: "¥2599",
                    tag: "新品上市",
                    img: "https://picsum.photos/id/21/800/600",
                    desc: "加斯顿B2人脸识别锁采用3D结构光人脸识别技术，夜间也能精准识别，识别距离0.3-1.5米，支持多种光线下快速识别。全自动锁体设计，识别成功后自动开锁，关门自动上锁，使用更便捷。",
                    params: {
                        "产品材质": "航空级铝合金",
                        "人脸容量": "50张",
                        "指纹容量": "100枚",
                        "密码容量": "50组",
                        "工作电压": "8V（锂电池）",
                        "待机时间": "500天",
                        "识别距离": "0.3-1.5米",
                        "工作温度": "-25℃~70℃",
                        "适用门厚": "40mm~120mm",
                        "开锁方式": "人脸、指纹、密码、刷卡、APP、钥匙"
                    }
                },
                3: {
                    name: "加斯顿C3基础款智能锁",
                    price: "¥899",
                    tag: "经济款",
                    img: "https://picsum.photos/id/22/800/600",
                    desc: "加斯顿C3基础款智能锁是一款高性价比的入门级智能锁，保留核心智能功能，去除冗余设计，适合预算有限的家庭使用。操作简单，安装方便，支持多种基础解锁方式，满足日常使用需求。",
                    params: {
                        "产品材质": "合金面板",
                        "指纹容量": "50枚",
                        "密码容量": "30组",
                        "工作电压": "6V（4节AA电池）",
                        "待机电流": "<60μA",
                        "工作温度": "-10℃~50℃",
                        "适用门厚": "40mm~100mm",
                        "开锁方式": "指纹、密码、钥匙"
                    }
                }
            };

            function openProductModal(id) {
                const product = products[id];
                if (!product) return;

                modalProductTitle.textContent = product.name;
                
                // 构建产品详情HTML
                let paramsHtml = '';
                for (const [key, value] of Object.entries(product.params)) {
                    paramsHtml += `
                        <tr>
                            <td>${key}</td>
                            <td>${value}</td>
                        </tr>
                    `;
                }

                modalProductContent.innerHTML = `
                    <div class="product-detail-img">
                        <img src="${product.img}" alt="${product.name}">
                    </div>
                    <div class="product-detail-info">
                        <div class="product-detail-price">${product.price}</div>
                        <span class="product-detail-tag">${product.tag}</span>
                        <p class="product-detail-desc">${product.desc}</p>
                        <div class="product-detail-params">
                            <h4>技术参数</h4>
                            <table>
                                ${paramsHtml}
                            </table>
                        </div>
                        <div style="display: flex; gap: 15px;">
                            <button class="btn btn-primary" style="flex: 1;">立即购买</button>
                            <button class="btn btn-outline" style="flex: 1;">加入购物车</button>
                        </div>
                    </div>
                `;

                productModal.classList.add('active');
                document.body.style.overflow = 'hidden';
            }

            function closeProductModal() {
                productModal.classList.remove('active');
                document.body.style.overflow = '';
            }

            viewProductBtns.forEach(btn => {
                btn.addEventListener('click', function() {
                    const id = this.getAttribute('data-id');
                    openProductModal(id);
                });
            });

            closeProduct.addEventListener('click', closeProductModal);
            productModal.addEventListener('click', function(e) {
                if (e.target === productModal) {
                    closeProductModal();
                }
            });

                // 3. 回到顶部按钮
            const backToTopBtn = document.getElementById('back-to-top');
        window.addEventListener('scroll', () => {
      if (window.scrollY > 300) {
        backToTopBtn.classList.remove('opacity-0', 'invisible');
        backToTopBtn.classList.add('opacity-100', 'visible');
      } else {
        backToTopBtn.classList.add('opacity-0', 'invisible');
        backToTopBtn.classList.remove('opacity-100', 'visible');
      }
    });
    backToTopBtn.addEventListener('click', () => {
      window.scrollTo({
        top: 0,
        behavior: 'smooth'
      });
    });

            // 滚动动画
            const sections = document.querySelectorAll('.section');
            
            function checkSections() {
                const triggerBottom = window.innerHeight * 0.8;
                
                sections.forEach(section => {
                    const sectionTop = section.getBoundingClientRect().top;
                    
                    if (sectionTop < triggerBottom) {
                        section.classList.add('active');
                    }
                });
            }

            window.addEventListener('scroll', checkSections);
            checkSections(); // 初始检查

            // 表单验证
            const contactForm = document.getElementById('contactForm');
            
            contactForm.addEventListener('submit', function(e) {
                e.preventDefault();
                let isValid = true;
                
                // 姓名验证
                const name = document.getElementById('name');
                if (!name.value.trim()) {
                    showError(name, '请输入姓名');
                    isValid = false;
                } else {
                    hideError(name);
                }
                
                // 电话验证
                const phone = document.getElementById('phone');
                const phoneReg = /^1[3-9]\d{9}$/;
                if (!phoneReg.test(phone.value.trim())) {
                    showError(phone, '请输入正确的手机号码');
                    isValid = false;
                } else {
                    hideError(phone);
                }
                
                // 产品选择验证
                const product = document.getElementById('product');
                if (!product.value) {
                    showError(product, '请选择产品');
                    isValid = false;
                } else {
                    hideError(product);
                }
                
                // 留言验证
                const message = document.getElementById('message');
                if (!message.value.trim()) {
                    showError(message, '请输入留言内容');
                    isValid = false;
                } else {
                    hideError(message);
                }
                
                if (isValid) {
                    // 表单提交逻辑
                    alert('留言提交成功，我们会尽快与您联系！');
                    contactForm.reset();
                }
            });

            // 登录表单验证
            const loginForm = document.getElementById('loginForm');
            
            loginForm.addEventListener('submit', function(e) {
                e.preventDefault();
                let isValid = true;
                
                // 手机号验证
                const loginPhone = document.getElementById('loginPhone');
                const phoneReg = /^1[3-9]\d{9}$/;
                if (!phoneReg.test(loginPhone.value.trim())) {
                    showError(loginPhone, '请输入正确的手机号码');
                    isValid = false;
                } else {
                    hideError(loginPhone);
                }
                
                // 密码验证
                const loginPwd = document.getElementById('loginPwd');
                if (loginPwd.value.length < 6) {
                    showError(loginPwd, '密码长度不少于6位');
                    isValid = false;
                } else {
                    hideError(loginPwd);
                }
                
                if (isValid) {
                    // 登录逻辑
                    alert('登录成功！');
                    closeLoginModal();
                    loginForm.reset();
                }
            });

            // 错误提示显示/隐藏
            function showError(element, text) {
                const tip = element.nextElementSibling;
                tip.textContent = text;
                tip.classList.add('active');
                element.style.borderColor = '#ef4444';
            }

            function hideError(element) {
                const tip = element.nextElementSibling;
                tip.classList.remove('active');
                element.style.borderColor = '#ddd';
            }
        });
    </script>
</body>
</html>

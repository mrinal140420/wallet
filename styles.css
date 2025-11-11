// Youth Wallet - Campus Wallet PWA
// Pure JavaScript Implementation

// Application State
const state = {
    currentPage: 'dashboard',
    balance: 125000,
    dailyLimit: 10000,
    qrPayment: {
        step: 'scan',
        otp: '',
        billData: {
            vendor: 'Campus Cafeteria',
            amount: 2500,
            billId: 'BILL-12345',
            expiresIn: 180
        }
    },
    recharge: {
        step: 'amount',
        amount: '',
        paymentMethod: 'upi'
    },
    settings: {
        dailyLimit: 10000,
        perTransactionLimit: 5000,
        notifications: {
            recharge: true,
            spend: true,
            lowBalance: true,
            dailyReport: false
        }
    }
};

// SVG Icons as strings
const icons = {
    gem: '<svg class="w-12 h-12 text-[--color-secondary] opacity-80" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z"/></svg>',
    shieldCheck: '<svg class="w-4 h-4 mr-1 text-[--color-secondary]" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z"/></svg>',
    scanLine: '<svg class="w-6 h-6 mb-1" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v1m6 11h2m-6 0h-2v4m0-11v3m0 0h.01M12 12h4.01M16 20h4M4 12h4m12 0h.01M5 8h2a1 1 0 001-1V5a1 1 0 00-1-1H5a1 1 0 00-1 1v2a1 1 0 001 1zm12 0h2a1 1 0 001-1V5a1 1 0 00-1-1h-2a1 1 0 00-1 1v2a1 1 0 001 1zM5 20h2a1 1 0 001-1v-2a1 1 0 00-1-1H5a1 1 0 00-1 1v2a1 1 0 001 1z"/></svg>',
    wallet: '<svg class="w-6 h-6 mb-1" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 10h18M7 15h1m4 0h1m-7 4h12a3 3 0 003-3V8a3 3 0 00-3-3H6a3 3 0 00-3 3v8a3 3 0 003 3z"/></svg>',
    listChecks: '<svg class="w-6 h-6 mb-1" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2m-6 9l2 2 4-4"/></svg>',
    bell: '<svg class="w-6 h-6 mb-1" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9"/></svg>',
    coffee: '<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z"/></svg>',
    heart: '<svg class="w-5 h-5 fill-current" fill="currentColor" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z"/></svg>',
    book: '<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253"/></svg>',
    camera: '<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 9a2 2 0 012-2h.93a2 2 0 001.664-.89l.812-1.22A2 2 0 0110.07 4h3.86a2 2 0 011.664.89l.812 1.22A2 2 0 0018.07 7H19a2 2 0 012 2v9a2 2 0 01-2 2H5a2 2 0 01-2-2V9z"/><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 13a3 3 0 11-6 0 3 3 0 016 0z"/></svg>',
    alertCircle: '<svg class="h-4 w-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4m0 4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"/></svg>',
    checkCircle2: '<svg class="w-12 h-12" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"/></svg>',
    smartphone: '<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 18h.01M8 21h8a2 2 0 002-2V5a2 2 0 00-2-2H8a2 2 0 00-2 2v14a2 2 0 002 2z"/></svg>',
    creditCard: '<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 10h18M7 15h1m4 0h1m-7 4h12a3 3 0 003-3V8a3 3 0 00-3-3H6a3 3 0 00-3 3v8a3 3 0 003 3z"/></svg>',
    building2: '<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 21V5a2 2 0 00-2-2H7a2 2 0 00-2 2v16m14 0h2m-2 0h-5m-9 0H3m2 0h5M9 7h1m-1 4h1m4-4h1m-1 4h1m-5 10v-5a1 1 0 011-1h2a1 1 0 011 1v5m-4 0h4"/></svg>',
    arrowRight: '<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6"/></svg>',
    user: '<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"/></svg>',
    mail: '<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/></svg>',
    phone: '<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"/></svg>',
    calendar: '<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"/></svg>',
    mapPin: '<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"/><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"/></svg>',
    hash: '<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 20l4-16m2 16l4-16M6 9h14M4 15h14"/></svg>',
    shield: '<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z"/></svg>',
    lock: '<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8z"/></svg>',
    eye: '<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"/><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z"/></svg>',
    alertTriangle: '<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z"/></svg>',
    info: '<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"/></svg>',
    x: '<svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/></svg>',
    search: '<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"/></svg>',
    download: '<svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4"/></svg>',
    utensils: '<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z"/></svg>',
    shoppingBag: '<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 11V7a4 4 0 00-8 0v4M5 9h14l1 12H4L5 9z"/></svg>',
    bus: '<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7h12m0 0l-4-4m4 4l-4 4m0 6H4m0 0l4 4m-4-4l4-4"/></svg>'
};

// Transaction data
const transactions = [
    { id: '1', title: 'Campus Cafeteria', description: 'Today, 1:45 PM (Lunch! 🍔)', amount: -2500, type: 'spend', icon: 'coffee' },
    { id: '2', title: 'Recharge from Guardian', description: 'Yesterday, 9:00 AM (Thanks Mom/Dad! 🙏)', amount: 50000, type: 'recharge', icon: 'heart' },
    { id: '3', title: 'Book Store Purchase', description: '2 days ago (Textbooks are expensive 😭)', amount: -15000, type: 'spend', icon: 'book' }
];

// Full transaction data for transactions page
const allTransactions = [
    { id: 'TXN001', title: 'Campus Cafeteria', description: 'Lunch purchase', amount: -2500, type: 'spend', category: 'Food', date: 'Nov 10, 2025', time: '1:45 PM', status: 'completed' },
    { id: 'TXN002', title: 'Recharge from Guardian', description: 'Monthly allowance', amount: 50000, type: 'recharge', category: 'Recharge', date: 'Nov 9, 2025', time: '9:00 AM', status: 'completed' },
    { id: 'TXN003', title: 'Book Store Purchase', description: 'Textbooks for semester', amount: -15000, type: 'spend', category: 'Books', date: 'Nov 8, 2025', time: '3:30 PM', status: 'completed' },
    { id: 'TXN004', title: 'Campus Canteen', description: 'Snacks and beverages', amount: -1200, type: 'spend', category: 'Food', date: 'Nov 8, 2025', time: '11:15 AM', status: 'completed' },
    { id: 'TXN005', title: 'Library Fine Refund', description: 'Late return fee reversed', amount: 500, type: 'refund', category: 'Refund', date: 'Nov 7, 2025', time: '2:00 PM', status: 'completed' },
    { id: 'TXN006', title: 'Stationary Shop', description: 'Notebooks and pens', amount: -800, type: 'spend', category: 'Supplies', date: 'Nov 6, 2025', time: '4:20 PM', status: 'completed' },
    { id: 'TXN007', title: 'Campus Shuttle', description: 'Weekly bus pass', amount: -1500, type: 'spend', category: 'Transport', date: 'Nov 5, 2025', time: '8:00 AM', status: 'completed' },
    { id: 'TXN008', title: 'UPI Recharge', description: 'Self recharge via UPI', amount: 10000, type: 'recharge', category: 'Recharge', date: 'Nov 4, 2025', time: '6:30 PM', status: 'completed' }
];

// Alerts data
const alerts = [
    { id: '1', type: 'warning', title: 'Approaching Daily Limit', message: "You've spent 8,500 Cr today. Your daily limit is 10,000 Cr.", timestamp: '2 hours ago', read: false },
    { id: '2', type: 'success', title: 'Recharge Successful', message: 'Your wallet was recharged with 50,000 Cr from Guardian.', timestamp: 'Yesterday at 9:00 AM', read: false },
    { id: '3', type: 'info', title: 'New Feature Available', message: 'You can now set custom spending categories and track habits!', timestamp: '2 days ago', read: true },
    { id: '4', type: 'success', title: 'Payment Successful', message: 'Your payment of 2,500 Cr at Campus Cafeteria was successful.', timestamp: '3 days ago', read: true },
    { id: '5', type: 'warning', title: 'Low Balance Alert', message: 'Your balance is below 5,000 Cr. Consider recharging soon.', timestamp: '5 days ago', read: true }
];

// Helper Functions
function formatNumber(num) {
    return num.toLocaleString();
}

function navigate(page) {
    state.currentPage = page;
    updateHeader();
    render();
}

function updateHeader() {
    const titles = {
        'dashboard': 'Wallet Dashboard 🚀',
        'qr-payment': 'QR Payment',
        'recharge': 'Recharge Wallet',
        'transactions': 'Transaction History',
        'alerts': 'Alerts & Notifications',
        'profile': 'My Profile',
        'settings': 'Settings'
    };
    
    document.getElementById('page-title').textContent = titles[state.currentPage] || 'Wallet Dashboard 🚀';
    
    const backButton = document.getElementById('back-button');
    if (state.currentPage === 'dashboard') {
        backButton.style.display = 'none';
    } else {
        backButton.style.display = 'flex';
    }
}

// Page Renderers
function renderDashboard() {
    return `
        <!-- Balance Card -->
        <section id="balance-card" class="card-bg p-6 sm:p-8 rounded-3xl mb-8 border-4 border-white shadow-xl">
            <div class="flex justify-between items-center">
                <div>
                    <p class="text-xl text-gray-500">Your Campus Credits</p>
                    <div class="flex items-baseline mt-1">
                        <span id="current-balance" class="text-6xl sm:text-7xl font-extrabold text-[--color-text] animate-pop transition duration-300">
                            ${formatNumber(state.balance)}
                        </span>
                        <span class="text-3xl font-semibold ml-2 text-[--color-primary]">✨ Cr</span>
                    </div>
                </div>
                ${icons.gem}
            </div>
            <p class="text-sm text-gray-500 mt-4 flex items-center">
                ${icons.shieldCheck}
                Daily Limit: <strong class="ml-1">${formatNumber(state.dailyLimit)} Cr</strong> (You're doing great!)
            </p>
        </section>

        <!-- Quick Actions -->
        <section class="grid grid-cols-2 sm:grid-cols-4 gap-4 mb-10">
            <button class="btn-primary p-4 rounded-2xl shadow-lg flex flex-col items-center text-white hover:scale-105 transition duration-200" onclick="navigate('qr-payment')">
                ${icons.scanLine}
                <span class="font-semibold text-sm sm:text-base">QR Pay!</span>
            </button>
            
            <button class="btn-primary p-4 rounded-2xl shadow-lg flex flex-col items-center text-white hover:scale-105 transition duration-200" onclick="navigate('recharge')">
                ${icons.wallet}
                <span class="font-semibold text-sm sm:text-base">Recharge 🎁</span>
            </button>
            
            <button class="btn-secondary-ring p-4 rounded-2xl shadow-md flex flex-col items-center hover:scale-105 transition duration-200" onclick="navigate('transactions')">
                ${icons.listChecks}
                <span class="font-semibold text-sm sm:text-base">My Habits</span>
            </button>
            
            <button class="btn-secondary-ring p-4 rounded-2xl shadow-md flex flex-col items-center hover:scale-105 transition duration-200" onclick="navigate('alerts')">
                ${icons.bell}
                <span class="font-semibold text-sm sm:text-base">Alerts!</span>
            </button>
        </section>

        <!-- Recent Transactions -->
        <section class="card-bg p-6 rounded-3xl shadow-xl">
            <h2 class="text-xl font-bold mb-4 text-[--color-primary]">Last 3 Moves</h2>
            <div id="transaction-list" class="space-y-3">
                ${transactions.map(txn => {
                    const isSpend = txn.type === 'spend';
                    const iconHtml = icons[txn.icon];
                    const bgClass = isSpend ? 'bg-red-400/20 text-red-700' : 'bg-[--color-secondary]/20 text-[--color-secondary]';
                    const amountClass = isSpend ? 'text-red-600' : 'text-[--color-secondary]';
                    const fillClass = !isSpend ? 'fill-current' : '';
                    
                    return `
                        <div class="flex justify-between items-center py-3 px-3 card-bg rounded-xl shadow-sm border border-gray-100 transition duration-150 hover:shadow-lg hover:border-[--color-primary]">
                            <div class="flex items-center space-x-3">
                                <div class="w-10 h-10 flex items-center justify-center rounded-full ${bgClass}">
                                    <div class="${fillClass}">${iconHtml}</div>
                                </div>
                                <div>
                                    <p class="font-semibold text-[--color-text]">${txn.title}</p>
                                    <p class="text-xs text-gray-500">${txn.description}</p>
                                </div>
                            </div>
                            <p class="font-extrabold text-lg ${amountClass}">
                                ${isSpend ? '- ' : '+ '}${formatNumber(Math.abs(txn.amount))} Cr
                            </p>
                        </div>
                    `;
                }).join('')}
                
                <div class="pt-4 text-center">
                    <button class="btn-secondary-ring px-6 py-2 rounded-full font-semibold text-sm hover:text-white hover:scale-102" onclick="navigate('transactions')">
                        View Full History →
                    </button>
                </div>
            </div>
        </section>
    `;
}

function renderQRPayment() {
    const step = state.qrPayment.step;
    
    if (step === 'scan') {
        return `
            <div class="space-y-6">
                <div class="card-bg p-12 rounded-3xl shadow-xl text-center">
                    <div class="w-32 h-32 mx-auto mb-6 bg-[--color-primary]/10 rounded-full flex items-center justify-center">
                        <svg class="w-16 h-16 text-[--color-primary]" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v1m6 11h2m-6 0h-2v4m0-11v3m0 0h.01M12 12h4.01M16 20h4M4 12h4m12 0h.01M5 8h2a1 1 0 001-1V5a1 1 0 00-1-1H5a1 1 0 00-1 1v2a1 1 0 001 1zm12 0h2a1 1 0 001-1V5a1 1 0 00-1-1h-2a1 1 0 00-1 1v2a1 1 0 001 1zM5 20h2a1 1 0 001-1v-2a1 1 0 00-1-1H5a1 1 0 00-1 1v2a1 1 0 001 1z"/>
                        </svg>
                    </div>
                    <h2 class="text-2xl font-bold mb-2">Scan QR Code</h2>
                    <p class="text-gray-600 mb-8">Point your camera at the vendor's QR code to start payment</p>
                    
                    <button class="btn-primary px-8 py-6 rounded-2xl text-white text-lg font-semibold shadow-lg flex items-center gap-2 mx-auto" onclick="setQRStep('preview')">
                        ${icons.camera}
                        Open Camera
                    </button>

                    <div class="mt-6 pt-6 border-t">
                        <p class="text-sm text-gray-500 mb-3">Or enter code manually</p>
                        <input type="text" placeholder="Enter 6-digit code" class="max-w-xs mx-auto">
                    </div>
                </div>

                <div class="alert border-[--color-secondary] bg-[--color-secondary]/5">
                    <div class="text-[--color-secondary]">${icons.alertCircle}</div>
                    <p class="text-[--color-secondary]">Make sure the QR code is well lit and within the camera frame</p>
                </div>
            </div>
        `;
    } else if (step === 'preview') {
        const bill = state.qrPayment.billData;
        return `
            <div class="space-y-6">
                <div class="card-bg p-8 rounded-3xl shadow-xl">
                    <div class="text-center mb-6">
                        <h2 class="text-2xl font-bold mb-2">Confirm Payment</h2>
                        <p class="text-gray-600">Review the details before proceeding</p>
                    </div>

                    <div class="space-y-4 mb-8">
                        <div class="flex justify-between items-center p-4 bg-gray-50 rounded-xl">
                            <span class="text-gray-600">Vendor</span>
                            <span class="font-semibold">${bill.vendor}</span>
                        </div>
                        
                        <div class="flex justify-between items-center p-4 bg-gray-50 rounded-xl">
                            <span class="text-gray-600">Bill ID</span>
                            <span class="font-mono text-sm">${bill.billId}</span>
                        </div>
                        
                        <div class="flex justify-between items-center p-6 bg-gradient-to-br from-[--color-primary]/10 to-[--color-primary]/5 rounded-2xl border-2 border-[--color-primary]">
                            <span class="text-lg font-semibold">Amount</span>
                            <span class="text-3xl font-bold text-[--color-primary]">${formatNumber(bill.amount)} Cr</span>
                        </div>

                        <div class="alert border-yellow-400 bg-yellow-50">
                            <div class="text-yellow-600">${icons.alertCircle}</div>
                            <p class="text-yellow-800">This QR code expires in ${Math.floor(bill.expiresIn / 60)}:${(bill.expiresIn % 60).toString().padStart(2, '0')} minutes</p>
                        </div>
                    </div>

                    <div class="flex gap-3">
                        <button class="flex-1 btn-secondary-ring px-6 py-3 rounded-2xl font-semibold" onclick="setQRStep('scan')">
                            Cancel
                        </button>
                        <button class="flex-1 btn-primary px-6 py-3 rounded-2xl text-white font-semibold shadow-lg" onclick="setQRStep('otp')">
                            Continue to OTP
                        </button>
                    </div>
                </div>
            </div>
        `;
    } else if (step === 'otp') {
        return `
            <div class="space-y-6">
                <div class="card-bg p-8 rounded-3xl shadow-xl">
                    <div class="text-center mb-8">
                        <h2 class="text-2xl font-bold mb-2">Enter OTP</h2>
                        <p class="text-gray-600">Enter the 6-digit code to confirm payment</p>
                        <p class="text-sm text-gray-500 mt-2">OTP sent to your registered mobile number</p>
                    </div>

                    <div class="otp-container">
                        ${[0,1,2,3,4,5].map(i => `<input type="text" maxlength="1" class="otp-input" id="otp-${i}" oninput="handleOTPInput(event, ${i})">`).join('')}
                    </div>

                    <div class="alert mb-6">
                        ${icons.alertCircle}
                        <p>You have 3 attempts remaining. After 3 failed attempts, your wallet will be locked for 15 minutes.</p>
                    </div>

                    <div class="flex gap-3">
                        <button class="flex-1 btn-secondary-ring px-6 py-3 rounded-2xl font-semibold" onclick="setQRStep('preview')">
                            Back
                        </button>
                        <button id="verify-btn" class="flex-1 btn-primary px-6 py-3 rounded-2xl text-white font-semibold shadow-lg" onclick="setQRStep('success')" disabled>
                            Verify & Pay
                        </button>
                    </div>

                    <div class="text-center mt-4">
                        <button class="text-[--color-secondary] font-semibold">
                            Resend OTP (00:30)
                        </button>
                    </div>
                </div>
            </div>
        `;
    } else if (step === 'success') {
        const bill = state.qrPayment.billData;
        const txnId = 'TXN-' + Math.random().toString(36).substr(2, 9).toUpperCase();
        const newBalance = state.balance - bill.amount;
        
        return `
            <div class="space-y-6">
                <div class="card-bg p-12 rounded-3xl shadow-xl text-center">
                    <div class="w-24 h-24 mx-auto mb-6 bg-green-100 rounded-full flex items-center justify-center">
                        <svg class="w-12 h-12 text-green-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"/>
                        </svg>
                    </div>
                    <h2 class="text-3xl font-bold mb-2" style="color: #059669;">Payment Successful! 🎉</h2>
                    <p class="text-gray-600 mb-8">Your payment has been processed successfully</p>
                    
                    <div class="space-y-3 mb-8">
                        <div class="flex justify-between items-center p-4 bg-gray-50 rounded-xl">
                            <span class="text-gray-600">Amount Paid</span>
                            <span class="text-xl font-bold" style="color: #059669;">${formatNumber(bill.amount)} Cr</span>
                        </div>
                        
                        <div class="flex justify-between items-center p-4 bg-gray-50 rounded-xl">
                            <span class="text-gray-600">Vendor</span>
                            <span class="font-semibold">${bill.vendor}</span>
                        </div>
                        
                        <div class="flex justify-between items-center p-4 bg-gray-50 rounded-xl">
                            <span class="text-gray-600">Transaction ID</span>
                            <span class="font-mono text-sm">${txnId}</span>
                        </div>
                        
                        <div class="flex justify-between items-center p-4 bg-[--color-primary]/10 rounded-xl">
                            <span class="text-gray-600">New Balance</span>
                            <span class="text-xl font-bold text-[--color-primary]">${formatNumber(newBalance)} Cr</span>
                        </div>
                    </div>

                    <div class="flex gap-3">
                        <button class="flex-1 btn-secondary-ring px-6 py-3 rounded-2xl font-semibold">
                            Download Receipt
                        </button>
                        <button class="flex-1 btn-primary px-6 py-3 rounded-2xl text-white font-semibold shadow-lg" onclick="setQRStep('scan')">
                            Make Another Payment
                        </button>
                    </div>
                </div>
            </div>
        `;
    }
}

function renderRecharge() {
    const step = state.recharge.step;
    
    if (step === 'amount') {
        const quickAmounts = [1000, 2500, 5000, 10000, 25000, 50000];
        const amount = state.recharge.amount;
        
        return `
            <div class="space-y-6">
                <div class="card-bg p-8 rounded-3xl shadow-xl">
                    <h2 class="text-2xl font-bold mb-6">Select Recharge Amount</h2>

                    <div class="grid grid-cols-3 gap-3 mb-6">
                        ${quickAmounts.map(amt => `
                            <button class="${amount === amt.toString() ? 'btn-primary text-white' : 'border-2 bg-white hover:border-[--color-primary]'}" 
                                    style="height: 4rem; font-size: 1.125rem; font-weight: 600; border-radius: 0.75rem; ${amount === amt.toString() ? '' : 'border-color: #E5E7EB;'}"
                                    onclick="setRechargeAmount('${amt}')">
                                ${formatNumber(amt)} Cr
                            </button>
                        `).join('')}
                    </div>

                    <div class="space-y-2 mb-6">
                        <label class="font-semibold">Or enter custom amount</label>
                        <div style="position: relative;">
                            <input type="number" placeholder="Enter amount" value="${amount}" class="h-14 text-lg pr-12" style="width: 100%; padding-right: 3rem;" oninput="setRechargeAmount(this.value)">
                            <span style="position: absolute; right: 1rem; top: 50%; transform: translateY(-50%); color: #6B7280; font-weight: 600;">Cr</span>
                        </div>
                        <p class="text-sm text-gray-500">
                            Minimum: 500 Cr • Maximum: 50,000 Cr
                        </p>
                    </div>

                    ${amount ? `
                        <div class="p-4 bg-gradient-to-br from-[--color-primary]/10 to-[--color-primary]/5 rounded-2xl border-2 border-[--color-primary] mb-6">
                            <div class="flex justify-between items-center">
                                <span class="text-gray-600">You will receive</span>
                                <span class="text-2xl font-bold text-[--color-primary]">
                                    ${formatNumber(parseInt(amount) * 1)} Credits
                                </span>
                            </div>
                            <p class="text-xs text-gray-500 mt-2">Conversion rate: ₹1 = 1 Credit</p>
                        </div>
                    ` : ''}

                    <button class="btn-primary w-full px-8 py-6 rounded-2xl text-white text-lg font-semibold shadow-lg flex items-center justify-center gap-2" 
                            onclick="setRechargeStep('method')"
                            ${!amount || parseInt(amount) < 500 ? 'disabled' : ''}>
                        Continue to Payment
                        ${icons.arrowRight}
                    </button>
                </div>

                <div class="card-bg p-6 rounded-2xl shadow-md">
                    <h3 class="font-bold mb-4">Recent Recharges</h3>
                    <div class="space-y-2">
                        <div class="flex justify-between items-center p-3 bg-gray-50 rounded-xl">
                            <div>
                                <p class="font-semibold">Guardian Transfer</p>
                                <p class="text-xs text-gray-500">Nov 9, 2025</p>
                            </div>
                            <p class="font-bold" style="color: #059669;">+ 50,000 Cr</p>
                        </div>
                        <div class="flex justify-between items-center p-3 bg-gray-50 rounded-xl">
                            <div>
                                <p class="font-semibold">UPI Payment</p>
                                <p class="text-xs text-gray-500">Nov 4, 2025</p>
                            </div>
                            <p class="font-bold" style="color: #059669;">+ 10,000 Cr</p>
                        </div>
                    </div>
                </div>
            </div>
        `;
    } else if (step === 'method') {
        const amount = state.recharge.amount;
        const method = state.recharge.paymentMethod;
        
        const methods = [
            { id: 'upi', icon: icons.smartphone, title: 'UPI Payment', desc: 'Google Pay, PhonePe, Paytm, etc.' },
            { id: 'card', icon: icons.creditCard, title: 'Credit / Debit Card', desc: 'Visa, Mastercard, RuPay' },
            { id: 'netbanking', icon: icons.building2, title: 'Net Banking', desc: 'All major banks supported' },
            { id: 'cash', icon: icons.wallet, title: 'Cash Counter', desc: 'Visit campus cash counter' }
        ];
        
        return `
            <div class="space-y-6">
                <div class="card-bg p-8 rounded-3xl shadow-xl">
                    <h2 class="text-2xl font-bold mb-2">Select Payment Method</h2>
                    <p class="text-gray-600 mb-6">Choose how you want to recharge</p>

                    <div class="p-4 bg-gray-50 rounded-2xl mb-6">
                        <div class="flex justify-between items-center">
                            <span class="text-gray-600">Recharge Amount</span>
                            <span class="text-2xl font-bold text-[--color-primary]">${formatNumber(parseInt(amount))} Cr</span>
                        </div>
                    </div>

                    <div class="space-y-3 mb-6">
                        ${methods.map(m => `
                            <div class="radio-item ${method === m.id ? 'selected' : ''}" onclick="setPaymentMethod('${m.id}')">
                                <input type="radio" name="payment-method" value="${m.id}" ${method === m.id ? 'checked' : ''}>
                                ${m.icon}
                                <div class="flex-1">
                                    <p class="font-semibold">${m.title}</p>
                                    <p class="text-sm text-gray-500">${m.desc}</p>
                                </div>
                                ${method === m.id ? `<svg class="w-5 h-5 text-[--color-primary]" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"/></svg>` : ''}
                            </div>
                        `).join('')}
                    </div>

                    <div class="flex gap-3">
                        <button class="flex-1 btn-secondary-ring px-6 py-3 rounded-2xl font-semibold" onclick="setRechargeStep('amount')">
                            Back
                        </button>
                        <button class="flex-1 btn-primary px-6 py-3 rounded-2xl text-white font-semibold shadow-lg" onclick="setRechargeStep('success')">
                            Proceed to Pay
                        </button>
                    </div>
                </div>
            </div>
        `;
    } else if (step === 'success') {
        const amount = parseInt(state.recharge.amount);
        const method = state.recharge.paymentMethod;
        const txnId = 'RCH-' + Math.random().toString(36).substr(2, 9).toUpperCase();
        const newBalance = state.balance + amount;
        
        return `
            <div class="space-y-6">
                <div class="card-bg p-12 rounded-3xl shadow-xl text-center">
                    <div class="w-24 h-24 mx-auto mb-6 bg-green-100 rounded-full flex items-center justify-center">
                        ${icons.checkCircle2}
                    </div>
                    <h2 class="text-3xl font-bold mb-2" style="color: #059669;">Recharge Successful! 🎉</h2>
                    <p class="text-gray-600 mb-8">Your wallet has been recharged successfully</p>

                    <div class="space-y-3 mb-8">
                        <div class="flex justify-between items-center p-4 bg-gray-50 rounded-xl">
                            <span class="text-gray-600">Amount Recharged</span>
                            <span class="text-xl font-bold" style="color: #059669;">${formatNumber(amount)} Cr</span>
                        </div>

                        <div class="flex justify-between items-center p-4 bg-gray-50 rounded-xl">
                            <span class="text-gray-600">Credits Added</span>
                            <span class="text-xl font-bold text-[--color-secondary]">${formatNumber(amount)} Cr</span>
                        </div>

                        <div class="flex justify-between items-center p-4 bg-gray-50 rounded-xl">
                            <span class="text-gray-600">Payment Method</span>
                            <span class="font-semibold" style="text-transform: capitalize;">${method}</span>
                        </div>

                        <div class="flex justify-between items-center p-4 bg-gray-50 rounded-xl">
                            <span class="text-gray-600">Transaction ID</span>
                            <span class="font-mono text-sm">${txnId}</span>
                        </div>

                        <div class="flex justify-between items-center p-4 bg-[--color-primary]/10 rounded-xl">
                            <span class="text-gray-600">New Balance</span>
                            <span class="text-2xl font-bold text-[--color-primary]">${formatNumber(newBalance)} Cr</span>
                        </div>
                    </div>

                    <div class="flex gap-3">
                        <button class="flex-1 btn-secondary-ring px-6 py-3 rounded-2xl font-semibold">
                            Download Receipt
                        </button>
                        <button class="flex-1 btn-primary px-6 py-3 rounded-2xl text-white font-semibold shadow-lg" onclick="resetRecharge()">
                            Recharge Again
                        </button>
                    </div>
                </div>
            </div>
        `;
    }
}

function renderTransactions() {
    const iconMap = {
        'Food': icons.utensils,
        'Books': icons.book,
        'Recharge': icons.heart,
        'Refund': icons.heart,
        'Supplies': icons.shoppingBag,
        'Transport': icons.bus
    };
    
    return `
        <div class="space-y-6">
            <!-- Summary Cards -->
            <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                <div class="card-bg p-6 rounded-2xl shadow-md" style="background: linear-gradient(135deg, #ECFDF5, #D1FAE5); border: 2px solid #A7F3D0;">
                    <p class="text-sm mb-1" style="color: #065F46;">Total Recharged</p>
                    <p class="text-3xl font-bold" style="color: #047857;">60,000 Cr</p>
                    <p class="text-xs mt-1" style="color: #059669;">This month</p>
                </div>
                
                <div class="card-bg p-6 rounded-2xl shadow-md" style="background: linear-gradient(135deg, #FEF2F2, #FEE2E2); border: 2px solid #FECACA;">
                    <p class="text-sm mb-1" style="color: #991B1B;">Total Spent</p>
                    <p class="text-3xl font-bold" style="color: #B91C1C;">21,500 Cr</p>
                    <p class="text-xs mt-1" style="color: #DC2626;">This month</p>
                </div>
                
                <div class="card-bg p-6 rounded-2xl shadow-md" style="background: linear-gradient(135deg, #EFF6FF, #DBEAFE); border: 2px solid #BFDBFE;">
                    <p class="text-sm mb-1" style="color: #1E3A8A;">Total Transactions</p>
                    <p class="text-3xl font-bold" style="color: #1E40AF;">47</p>
                    <p class="text-xs mt-1" style="color: #2563EB;">This month</p>
                </div>
            </div>

            <!-- Filters -->
            <div class="card-bg p-6 rounded-2xl shadow-md">
                <div class="flex flex-col md:flex-row gap-4">
                    <div class="flex-1" style="position: relative;">
                        <div style="position: absolute; left: 0.75rem; top: 50%; transform: translateY(-50%); color: #9CA3AF;">
                            ${icons.search}
                        </div>
                        <input type="text" placeholder="Search transactions..." class="bg-gray-50" style="width: 100%; padding-left: 2.5rem;" id="txn-search" oninput="filterTransactions()">
                    </div>
                    
                    <select class="bg-gray-50 md:w-[180px]" id="txn-filter" onchange="filterTransactions()">
                        <option value="all">All Transactions</option>
                        <option value="spend">Spending</option>
                        <option value="recharge">Recharges</option>
                        <option value="refund">Refunds</option>
                    </select>

                    <button class="btn-primary px-6 py-2 rounded-xl text-white font-semibold shadow-lg flex items-center gap-2">
                        ${icons.download}
                        Export CSV
                    </button>
                </div>
            </div>

            <!-- Transactions List -->
            <div class="card-bg p-6 rounded-3xl shadow-xl">
                <div class="space-y-3" id="txn-list">
                    ${allTransactions.map(txn => {
                        const icon = iconMap[txn.category] || icons.coffee;
                        const isPositive = txn.amount > 0;
                        const bgColor = isPositive ? '#ECFDF5' : '#FEF2F2';
                        const iconColor = isPositive ? '#059669' : '#DC2626';
                        const amountColor = isPositive ? '#059669' : '#DC2626';
                        
                        return `
                            <div class="flex justify-between items-center p-4 bg-gray-50 rounded-xl transition hover:shadow-md" style="cursor: pointer;">
                                <div class="flex items-center gap-4">
                                    <div class="w-12 h-12 flex items-center justify-center rounded-full" style="background-color: ${bgColor}; color: ${iconColor};">
                                        ${icon}
                                    </div>
                                    
                                    <div>
                                        <div class="flex items-center gap-2">
                                            <p class="font-semibold text-[--color-text]">${txn.title}</p>
                                            <span class="badge badge-outline" style="font-size: 0.75rem;">
                                                ${txn.category}
                                            </span>
                                        </div>
                                        <p class="text-sm text-gray-500">${txn.description}</p>
                                        <p class="text-xs text-gray-400">${txn.date} at ${txn.time} • ${txn.id}</p>
                                    </div>
                                </div>
                                
                                <div style="text-align: right;">
                                    <p class="text-xl font-bold" style="color: ${amountColor};">
                                        ${isPositive ? '+' : ''} ${formatNumber(Math.abs(txn.amount))} Cr
                                    </p>
                                    <span class="badge" style="margin-top: 0.25rem; background-color: #D1FAE5; color: #065F46;">
                                        ${txn.status}
                                    </span>
                                </div>
                            </div>
                        `;
                    }).join('')}
                </div>
            </div>
        </div>
    `;
}

function renderProfile() {
    return `
        <div class="space-y-8">
            <!-- Profile Header Card -->
            <div class="card-bg p-8 rounded-3xl shadow-xl">
                <div class="flex flex-col md:flex-row gap-8 items-start">
                    <div class="flex flex-col items-center gap-4">
                        <div class="w-32 h-32 border-4 border-[--color-primary] rounded-full flex items-center justify-center bg-[--color-primary] text-white font-bold" style="font-size: 2.25rem;">
                            SA
                        </div>
                        <button class="btn-primary px-6 py-2 rounded-full text-white font-semibold">
                            Change Photo
                        </button>
                    </div>

                    <div class="flex-1" style="width: 100%;">
                        <div class="mb-6">
                            <h2 class="text-2xl font-bold text-[--color-text]">Student A</h2>
                            <p class="text-gray-500">Student ID: 00123</p>
                            <div class="flex gap-2 mt-2">
                                <span class="badge" style="background-color: #D1FAE5; color: #065F46;">Active</span>
                                <span class="badge" style="background-color: #DBEAFE; color: #1E3A8A;">Verified</span>
                            </div>
                        </div>

                        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                            <div class="flex items-center gap-3 p-3 bg-gray-50 rounded-xl">
                                <div class="text-[--color-primary]">${icons.mail}</div>
                                <div>
                                    <p class="text-xs text-gray-500">Email</p>
                                    <p class="font-semibold">student.a@campus.edu</p>
                                </div>
                            </div>

                            <div class="flex items-center gap-3 p-3 bg-gray-50 rounded-xl">
                                <div class="text-[--color-primary]">${icons.phone}</div>
                                <div>
                                    <p class="text-xs text-gray-500">Phone</p>
                                    <p class="font-semibold">+91 98765 43210</p>
                                </div>
                            </div>

                            <div class="flex items-center gap-3 p-3 bg-gray-50 rounded-xl">
                                <div class="text-[--color-primary]">${icons.calendar}</div>
                                <div>
                                    <p class="text-xs text-gray-500">Date of Birth</p>
                                    <p class="font-semibold">January 15, 2005</p>
                                </div>
                            </div>

                            <div class="flex items-center gap-3 p-3 bg-gray-50 rounded-xl">
                                <div class="text-[--color-primary]">${icons.hash}</div>
                                <div>
                                    <p class="text-xs text-gray-500">Roll Number</p>
                                    <p class="font-semibold">CS2023-0123</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Academic Information -->
            <div class="card-bg p-6 rounded-3xl shadow-xl">
                <h3 class="text-xl font-bold text-[--color-primary] mb-4">Academic Information</h3>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                    <div class="flex items-center gap-3 p-3 bg-gray-50 rounded-xl">
                        <div class="text-[--color-secondary]">${icons.mapPin}</div>
                        <div>
                            <p class="text-xs text-gray-500">Department</p>
                            <p class="font-semibold">Computer Science & Engineering</p>
                        </div>
                    </div>

                    <div class="flex items-center gap-3 p-3 bg-gray-50 rounded-xl">
                        <div class="text-[--color-secondary]">${icons.user}</div>
                        <div>
                            <p class="text-xs text-gray-500">Year / Semester</p>
                            <p class="font-semibold">3rd Year / 5th Semester</p>
                        </div>
                    </div>

                    <div class="flex items-center gap-3 p-3 bg-gray-50 rounded-xl">
                        <div class="text-[--color-secondary]">${icons.calendar}</div>
                        <div>
                            <p class="text-xs text-gray-500">Admission Date</p>
                            <p class="font-semibold">August 2023</p>
                        </div>
                    </div>

                    <div class="flex items-center gap-3 p-3 bg-gray-50 rounded-xl">
                        <div class="text-[--color-secondary]">${icons.shield}</div>
                        <div>
                            <p class="text-xs text-gray-500">Student Type</p>
                            <p class="font-semibold">Day Scholar</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Guardian Information -->
            <div class="card-bg p-6 rounded-3xl shadow-xl">
                <h3 class="text-xl font-bold text-[--color-primary] mb-4">Guardian Information</h3>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                    <div class="flex items-center gap-3 p-3 bg-gray-50 rounded-xl">
                        <div style="color: #9333EA;">${icons.user}</div>
                        <div>
                            <p class="text-xs text-gray-500">Guardian Name</p>
                            <p class="font-semibold">Mr. Parent A</p>
                        </div>
                    </div>

                    <div class="flex items-center gap-3 p-3 bg-gray-50 rounded-xl">
                        <div style="color: #9333EA;">${icons.phone}</div>
                        <div>
                            <p class="text-xs text-gray-500">Guardian Phone</p>
                            <p class="font-semibold">+91 98765 00000</p>
                        </div>
                    </div>

                    <div class="flex items-center gap-3 p-3 bg-gray-50 rounded-xl">
                        <div style="color: #9333EA;">${icons.mail}</div>
                        <div>
                            <p class="text-xs text-gray-500">Guardian Email</p>
                            <p class="font-semibold">parent.a@email.com</p>
                        </div>
                    </div>

                    <div class="flex items-center gap-3 p-3 bg-gray-50 rounded-xl">
                        <div style="color: #9333EA;">${icons.mapPin}</div>
                        <div>
                            <p class="text-xs text-gray-500">Relationship</p>
                            <p class="font-semibold">Father</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Action Buttons -->
            <div class="flex gap-4">
                <button class="btn-primary px-8 py-3 rounded-2xl text-white font-semibold shadow-lg">
                    Edit Profile
                </button>
                <button class="btn-secondary-ring px-8 py-3 rounded-2xl font-semibold shadow-md">
                    Change Password
                </button>
            </div>
        </div>
    `;
}

function renderAlerts() {
    const unreadCount = alerts.filter(a => !a.read).length;
    
    const iconMap = {
        'success': icons.checkCircle2,
        'warning': icons.alertTriangle,
        'info': icons.info
    };
    
    return `
        <div class="space-y-6">
            <div class="flex justify-between items-center mb-4">
                ${unreadCount > 0 ? `
                    <span class="badge" style="background-color: var(--color-primary); color: white;">
                        ${unreadCount} new alerts
                    </span>
                ` : '<div></div>'}
                <button class="btn-secondary-ring px-6 py-2 rounded-full font-semibold text-sm" style="margin-left: auto;">
                    Mark all as read
                </button>
            </div>

            <!-- Alert Summary Cards -->
            <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                <div class="card-bg p-4 rounded-2xl" style="background: linear-gradient(135deg, #ECFDF5, #D1FAE5); border: 2px solid #A7F3D0;">
                    <div class="flex items-center gap-3">
                        <div class="w-10 h-10 rounded-full flex items-center justify-center" style="background-color: #059669; color: white;">
                            ${icons.checkCircle2}
                        </div>
                        <div>
                            <p class="text-2xl font-bold" style="color: #047857;">12</p>
                            <p class="text-sm" style="color: #059669;">Success</p>
                        </div>
                    </div>
                </div>

                <div class="card-bg p-4 rounded-2xl" style="background: linear-gradient(135deg, #FFFBEB, #FEF3C7); border: 2px solid #FDE68A;">
                    <div class="flex items-center gap-3">
                        <div class="w-10 h-10 rounded-full flex items-center justify-center" style="background-color: #D97706; color: white;">
                            ${icons.alertTriangle}
                        </div>
                        <div>
                            <p class="text-2xl font-bold" style="color: #B45309;">3</p>
                            <p class="text-sm" style="color: #D97706;">Warnings</p>
                        </div>
                    </div>
                </div>

                <div class="card-bg p-4 rounded-2xl" style="background: linear-gradient(135deg, #EFF6FF, #DBEAFE); border: 2px solid #BFDBFE;">
                    <div class="flex items-center gap-3">
                        <div class="w-10 h-10 rounded-full flex items-center justify-center" style="background-color: #2563EB; color: white;">
                            ${icons.info}
                        </div>
                        <div>
                            <p class="text-2xl font-bold" style="color: #1E40AF;">5</p>
                            <p class="text-sm" style="color: #2563EB;">Info</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Alerts List -->
            <div class="card-bg p-6 rounded-3xl shadow-xl">
                <div class="space-y-3">
                    ${alerts.map(alert => {
                        const icon = iconMap[alert.type];
                        const colors = {
                            'success': { bg: '#ECFDF5', text: '#059669' },
                            'warning': { bg: '#FFFBEB', text: '#D97706' },
                            'info': { bg: '#EFF6FF', text: '#2563EB' }
                        }[alert.type];
                        
                        return `
                            <div class="flex items-start gap-4 p-4 rounded-xl transition" style="border: ${!alert.read ? '1px solid var(--color-primary)' : '1px solid #E5E7EB'}; background-color: ${!alert.read ? 'white' : '#F9FAFB'}; ${!alert.read ? 'box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);' : ''}">
                                <div class="w-10 h-10 rounded-full flex items-center justify-center" style="background-color: ${colors.bg}; color: ${colors.text}; flex-shrink: 0;">
                                    ${icon}
                                </div>

                                <div class="flex-1" style="min-width: 0;">
                                    <div class="flex items-start justify-between gap-2 mb-1">
                                        <h3 class="font-semibold text-[--color-text]">${alert.title}</h3>
                                        ${!alert.read ? '<span class="badge" style="background-color: var(--color-primary); color: white; font-size: 0.75rem;">New</span>' : ''}
                                    </div>
                                    <p class="text-sm text-gray-600 mb-2">${alert.message}</p>
                                    <p class="text-xs text-gray-400">${alert.timestamp}</p>
                                </div>

                                <button style="flex-shrink: 0; color: #9CA3AF; background: none; border: none; cursor: pointer; width: 2rem; height: 2rem; display: flex; align-items: center; justify-content: center;">
                                    ${icons.x}
                                </button>
                            </div>
                        `;
                    }).join('')}
                </div>
            </div>
        </div>
    `;
}

function renderSettings() {
    return `
        <div class="space-y-6">
            <!-- Spending Limits -->
            <div class="card-bg p-6 rounded-3xl shadow-xl">
                <div class="flex items-center gap-3 mb-6">
                    <div class="text-[--color-primary]">${icons.shield}</div>
                    <h2 class="text-xl font-bold">Spending Limits</h2>
                </div>

                <div class="space-y-8">
                    <div>
                        <div class="flex justify-between items-center mb-4">
                            <label class="font-semibold">Daily Spending Limit</label>
                            <span class="text-2xl font-bold text-[--color-primary]" id="daily-limit-display">
                                ${formatNumber(state.settings.dailyLimit)} Cr
                            </span>
                        </div>
                        <input type="range" min="1000" max="20000" step="500" value="${state.settings.dailyLimit}" oninput="updateDailyLimit(this.value)">
                        <p class="text-sm text-gray-500">
                            Set the maximum amount you can spend per day
                        </p>
                    </div>

                    <div>
                        <div class="flex justify-between items-center mb-4">
                            <label class="font-semibold">Per Transaction Limit</label>
                            <span class="text-2xl font-bold text-[--color-secondary]" id="txn-limit-display">
                                ${formatNumber(state.settings.perTransactionLimit)} Cr
                            </span>
                        </div>
                        <input type="range" min="500" max="10000" step="250" value="${state.settings.perTransactionLimit}" oninput="updateTxnLimit(this.value)">
                        <p class="text-sm text-gray-500">
                            Maximum amount for a single transaction
                        </p>
                    </div>

                    <div class="pt-4 border-t">
                        <button class="btn-primary px-8 py-3 rounded-2xl text-white font-semibold shadow-lg">
                            Save Limit Changes
                        </button>
                    </div>
                </div>
            </div>

            <!-- Notifications -->
            <div class="card-bg p-6 rounded-3xl shadow-xl">
                <div class="flex items-center gap-3 mb-6">
                    <div class="text-[--color-primary]">${icons.bell}</div>
                    <h2 class="text-xl font-bold">Notifications</h2>
                </div>

                <div class="space-y-4">
                    ${[
                        { key: 'recharge', title: 'Recharge Notifications', desc: 'Get notified when you receive credits' },
                        { key: 'spend', title: 'Spending Alerts', desc: 'Alert on every transaction' },
                        { key: 'lowBalance', title: 'Low Balance Warning', desc: 'Alert when balance is below 1,000 Cr' },
                        { key: 'dailyReport', title: 'Daily Summary Report', desc: 'Get daily spending summary via email' }
                    ].map(item => `
                        <div class="flex items-center justify-between p-4 bg-gray-50 rounded-xl">
                            <div>
                                <p class="font-semibold">${item.title}</p>
                                <p class="text-sm text-gray-500">${item.desc}</p>
                            </div>
                            <div class="switch-container">
                                <input type="checkbox" ${state.settings.notifications[item.key] ? 'checked' : ''} onchange="toggleNotification('${item.key}', this.checked)">
                                <span class="switch-slider"></span>
                            </div>
                        </div>
                    `).join('')}
                </div>
            </div>

            <!-- Security -->
            <div class="card-bg p-6 rounded-3xl shadow-xl">
                <div class="flex items-center gap-3 mb-6">
                    <div class="text-[--color-primary]">${icons.lock}</div>
                    <h2 class="text-xl font-bold">Security</h2>
                </div>

                <div class="space-y-4">
                    <div class="flex items-center justify-between p-4 bg-gray-50 rounded-xl">
                        <div class="flex items-center gap-3">
                            <div class="w-10 h-10 rounded-full flex items-center justify-center" style="background-color: #F3E8FF; color: #9333EA;">
                                ${icons.lock}
                            </div>
                            <div>
                                <p class="font-semibold">Change Password</p>
                                <p class="text-sm text-gray-500">Last changed 30 days ago</p>
                            </div>
                        </div>
                        <button class="btn-secondary-ring px-6 py-2 rounded-xl font-semibold text-sm">
                            Change
                        </button>
                    </div>

                    <div class="flex items-center justify-between p-4 bg-gray-50 rounded-xl">
                        <div class="flex items-center gap-3">
                            <div class="w-10 h-10 rounded-full flex items-center justify-center" style="background-color: #DBEAFE; color: #2563EB;">
                                ${icons.shield}
                            </div>
                            <div>
                                <p class="font-semibold">Two-Factor Authentication</p>
                                <p class="text-sm text-gray-500">Add extra security to your account</p>
                            </div>
                        </div>
                        <button class="btn-primary px-6 py-2 rounded-xl text-white font-semibold">
                            Enable
                        </button>
                    </div>

                    <div class="flex items-center justify-between p-4 bg-gray-50 rounded-xl">
                        <div class="flex items-center gap-3">
                            <div class="w-10 h-10 rounded-full flex items-center justify-center" style="background-color: #D1FAE5; color: #059669;">
                                ${icons.creditCard}
                            </div>
                            <div>
                                <p class="font-semibold">Payment PIN</p>
                                <p class="text-sm text-gray-500">Set a 4-digit PIN for quick payments</p>
                            </div>
                        </div>
                        <button class="btn-secondary-ring px-6 py-2 rounded-xl font-semibold text-sm">
                            Set PIN
                        </button>
                    </div>
                </div>
            </div>

            <!-- Privacy -->
            <div class="card-bg p-6 rounded-3xl shadow-xl">
                <div class="flex items-center gap-3 mb-6">
                    <div class="text-[--color-primary]">${icons.eye}</div>
                    <h2 class="text-xl font-bold">Privacy</h2>
                </div>

                <div class="space-y-4">
                    <div class="flex items-center justify-between p-4 bg-gray-50 rounded-xl">
                        <div>
                            <p class="font-semibold">Share Transaction Data</p>
                            <p class="text-sm text-gray-500">Allow guardians to view transactions</p>
                        </div>
                        <div class="switch-container">
                            <input type="checkbox" checked>
                            <span class="switch-slider"></span>
                        </div>
                    </div>

                    <div class="flex items-center justify-between p-4 bg-gray-50 rounded-xl">
                        <div>
                            <p class="font-semibold">Show Balance in App</p>
                            <p class="text-sm text-gray-500">Display balance on dashboard</p>
                        </div>
                        <div class="switch-container">
                            <input type="checkbox" checked>
                            <span class="switch-slider"></span>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Action Buttons -->
            <div class="flex gap-4">
                <button class="btn-primary px-8 py-3 rounded-2xl text-white font-semibold shadow-lg">
                    Save All Settings
                </button>
                <button class="btn-secondary-ring px-8 py-3 rounded-2xl font-semibold">
                    Reset to Defaults
                </button>
            </div>
        </div>
    `;
}

// Main render function
function render() {
    const mainContent = document.getElementById('main-content');
    
    switch (state.currentPage) {
        case 'dashboard':
            mainContent.innerHTML = renderDashboard();
            break;
        case 'qr-payment':
            mainContent.innerHTML = renderQRPayment();
            break;
        case 'recharge':
            mainContent.innerHTML = renderRecharge();
            break;
        case 'transactions':
            mainContent.innerHTML = renderTransactions();
            break;
        case 'profile':
            mainContent.innerHTML = renderProfile();
            break;
        case 'alerts':
            mainContent.innerHTML = renderAlerts();
            break;
        case 'settings':
            mainContent.innerHTML = renderSettings();
            break;
        default:
            mainContent.innerHTML = renderDashboard();
    }
}

// Event Handlers
function setQRStep(step) {
    state.qrPayment.step = step;
    render();
}

function handleOTPInput(event, index) {
    const value = event.target.value;
    
    if (value && index < 5) {
        const nextInput = document.getElementById(`otp-${index + 1}`);
        if (nextInput) nextInput.focus();
    }
    
    // Check if all fields are filled
    let otp = '';
    for (let i = 0; i < 6; i++) {
        const input = document.getElementById(`otp-${i}`);
        if (input) otp += input.value;
    }
    
    const verifyBtn = document.getElementById('verify-btn');
    if (verifyBtn) {
        verifyBtn.disabled = otp.length !== 6;
    }
}

function setRechargeAmount(amount) {
    state.recharge.amount = amount;
    render();
}

function setRechargeStep(step) {
    state.recharge.step = step;
    render();
}

function setPaymentMethod(method) {
    state.recharge.paymentMethod = method;
    render();
}

function resetRecharge() {
    state.recharge.step = 'amount';
    state.recharge.amount = '';
    render();
}

function filterTransactions() {
    // Transactions are already rendered with all data
    // This is a placeholder for filter functionality
    console.log('Filter transactions');
}

function updateDailyLimit(value) {
    state.settings.dailyLimit = parseInt(value);
    const display = document.getElementById('daily-limit-display');
    if (display) {
        display.textContent = formatNumber(value) + ' Cr';
    }
}

function updateTxnLimit(value) {
    state.settings.perTransactionLimit = parseInt(value);
    const display = document.getElementById('txn-limit-display');
    if (display) {
        display.textContent = formatNumber(value) + ' Cr';
    }
}

function toggleNotification(key, checked) {
    state.settings.notifications[key] = checked;
}

// Initialize app
document.addEventListener('DOMContentLoaded', () => {
    // Setup event listeners
    document.getElementById('back-button').addEventListener('click', () => navigate('dashboard'));
    document.getElementById('profile-btn').addEventListener('click', () => navigate('profile'));
    
    // Initial render
    render();
});

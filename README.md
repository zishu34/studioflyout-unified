// == UNIFIED STUDIOFLYOUT NEXT.JS + ADMIN PANEL PROJECT ==

// == STEP 1: app/layout.tsx == import './globals.css'; import { Inter } from 'next/font/google'; import Navbar from '@/components/Navbar';

const inter = Inter({ subsets: ['latin'] });

export const metadata = { title: 'StudioFlyout', description: 'Creative Studio for Edits & Design', };

export default function RootLayout({ children }) { return ( <html lang="en"> <body className={inter.className}> <Navbar /> <main className="min-h-screen p-4 bg-gray-50 text-gray-900"> {children} </main> </body> </html> ); }

// == STEP 2: app/page.tsx (Home) == export default function HomePage() { return ( <section className="text-center py-20"> <h1 className="text-4xl font-bold mb-4">Welcome to StudioFlyout</h1> <p className="text-lg">Creative Edits & Designs for Creators & Brands</p> </section> ); }

// == STEP 3: app/about/page.tsx == export default function AboutPage() { return ( <section className="py-10 max-w-2xl mx-auto"> <h2 className="text-3xl font-semibold mb-4">About StudioFlyout</h2> <p>We’re a creative agency specializing in edits and designs for modern creators, startups, and businesses.</p> </section> ); }

// == STEP 4: app/services/page.tsx == const services = ["Video Editing", "Thumbnail Design", "Branding", "Motion Graphics"]; export default function ServicesPage() { return ( <section className="py-10 max-w-3xl mx-auto"> <h2 className="text-3xl font-semibold mb-6">Our Services</h2> <ul className="grid grid-cols-1 sm:grid-cols-2 gap-4"> {services.map((s, i) => <li key={i} className="bg-white p-4 rounded-xl shadow">{s}</li>)} </ul> </section> ); }

// == STEP 5: app/portfolio/page.tsx == const projects = [ { title: "Sample Edit", desc: "A modern short-form reel for Instagram." }, { title: "Logo Design", desc: "Sleek and minimal brand logo." } ]; export default function PortfolioPage() { return ( <section className="py-10 max-w-3xl mx-auto"> <h2 className="text-3xl font-semibold mb-6">Our Work</h2> <div className="grid gap-4"> {projects.map((p, i) => ( <div key={i} className="bg-white p-4 rounded-xl shadow"> <h3 className="font-semibold text-xl">{p.title}</h3> <p>{p.desc}</p> </div> ))} </div> </section> ); }

// == STEP 6: app/contact/page.tsx == export default function ContactPage() { return ( <section className="py-10 max-w-lg mx-auto"> <h2 className="text-3xl font-semibold mb-6">Contact Us</h2> <p>Email: <a href="mailto:studioflyout@gmail.com" className="text-blue-500 underline">studioflyout@gmail.com</a></p> </section> ); }

// == STEP 7: app/admin/page.tsx == 'use client'; import { useState } from 'react';

const defaultServices = ["Video Editing", "Thumbnail Design"]; export default function AdminPage() { const [services, setServices] = useState(defaultServices); const [input, setInput] = useState("");

return ( <section className="py-10 max-w-xl mx-auto"> <h2 className="text-3xl font-bold mb-4">Admin Panel</h2> <input type="text" value={input} onChange={(e) => setInput(e.target.value)} placeholder="Add new service" className="border p-2 w-full rounded mb-2" /> <button onClick={() => { if (input) { setServices([...services, input]); setInput(""); } }} className="bg-black text-white px-4 py-2 rounded mb-4" > Add Service </button> <ul className="space-y-2"> {services.map((s, i) => ( <li key={i} className="bg-gray-100 p-2 rounded">{s}</li> ))} </ul> </section> ); }

// == STEP 8: components/Navbar.tsx == import Link from 'next/link';

const links = [ { href: '/', label: 'Home' }, { href: '/about', label: 'About' }, { href: '/services', label: 'Services' }, { href: '/portfolio', label: 'Portfolio' }, { href: '/contact', label: 'Contact' }, { href: '/admin', label: 'Admin' } ];

export default function Navbar() { return ( <nav className="bg-white border-b shadow px-6 py-4 flex justify-center gap-6"> {links.map(link => ( <Link key={link.href} href={link.href} className="hover:underline font-medium"> {link.label} </Link> ))} </nav> ); }

// == STEP 9: styles/globals.css == @tailwind base; @tailwind components; @tailwind utilities;

// == STEP 10: tailwind.config.ts == import type { Config } from 'tailwindcss'; const config: Config = { content: ['./app//*.{js,ts,jsx,tsx}', './components//*.{js,ts,jsx,tsx}'], theme: { extend: {}, }, plugins: [], }; export default config;

// == STEP 11: README (short) == /**

StudioFlyout Unified Web + Admin Panel

Stack: Next.js 14, Tailwind CSS

To run:

npm install

npm run dev */



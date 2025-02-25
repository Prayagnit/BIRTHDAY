import React, { useState, useEffect } from "react";
import { motion } from "framer-motion";
import Confetti from "react-confetti";

const images = [
  "/image1.jpg",
  "/image2.jpg",
  "/image3.jpg",
  "/image4.jpg"
];

const messages = [
  "Happy Birthday, My Love! 🎉 You're the light of my life and my greatest blessing.",
  "Every moment with you is a beautiful memory. Here's to many more! 💖",
  "Your kindness, laughter, and love make my world brighter every day! ✨",
  "Wishing you a day filled with love, happiness, and all your favorite things! 🎂🎈"
];

const BirthdayWish = () => {
  const [index, setIndex] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => {
      setIndex((prevIndex) => (prevIndex + 1) % images.length);
    }, 4000);
    return () => clearInterval(interval);
  }, []);

  return (
    <div className="flex flex-col items-center justify-center min-h-screen bg-pink-100 p-6 text-center">
      <Confetti numberOfPieces={100} />
      <motion.h1
        initial={{ opacity: 0, scale: 0.5 }}
        animate={{ opacity: 1, scale: 1 }}
        transition={{ duration: 1 }}
        className="text-4xl font-bold text-pink-600"
      >
        🎂 Happy Birthday, My Love! 🎈
      </motion.h1>
      <motion.img
        key={index}
        src={images[index]}
        alt="Memory"
        className="w-80 h-80 object-cover rounded-xl shadow-lg my-6"
        initial={{ opacity: 0, scale: 0.8 }}
        animate={{ opacity: 1, scale: 1 }}
        exit={{ opacity: 0, scale: 0.8 }}
        transition={{ duration: 1 }}
      />
      <motion.p
        key={index}
        className="text-lg text-gray-700 bg-white p-4 rounded-lg shadow-md"
        initial={{ opacity: 0, y: 20 }}
        animate={{ opacity: 1, y: 0 }}
        transition={{ duration: 1 }}
      >
        {messages[index]}
      </motion.p>
      <div className="mt-6 text-2xl">🎁 🎉 🎊 🍰</div>
    </div>
  );
};

export default BirthdayWish;

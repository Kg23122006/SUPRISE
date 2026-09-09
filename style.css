/* =========================================================
   FRIENDSHIP SURPRISE WEBSITE
   ========================================================= */

const birthdayData = {
  "03-19": {
    name: "DivyaShree.D (loosu)",
    message: "I'm genuinely grateful for every laugh, every random conversation, every annoying moment and every memory we've created together. 🫂❤️",
    quote: "I feel so lucky and grateful to have you as my best friend. 🫂✨\nYou have this beautiful way of making even the most ordinary days feel a little more special. 💖🥹\nI’m genuinely grateful for every laugh, every memory, and every moment we share. ✨",
    song: {
      title: "Kulirudha Pulla",
      artist: "Sid Sriram & Sangeetha Karuppiah",
      album: "Oththa Seruppu Size 7"
    }
  },
  "11-01": {
    name: "Aishvariya.S",
    message: "Some friendships quietly become one of the best parts of life, and you are one of the best parts of mine. 🫶✨",
    quote: "Some friendships quietly become one of the best parts of life. 🫶",
    song: {
      title: "Aley Aley Dhostu",
      artist: "Yuvan Shankar Raja",
      album: "Kanda Naal Mudha"
    }
  },
  "08-16": {
    name: "Sanjay.S",
    message: "You make life feel lighter, brighter, and a little more fun. I’m so glad you are in my life. ❤️",
    quote: "Some people enter your life and somehow make everything brighter. ❤️",
    song: {
      title: "Jigiri Dosthu",
      artist: "Jaya Moorthy, Anthakudi Ilayaraja",
      album: "Namma Veettu Pillai"
    }
  },
  "10-06": {
    name: "Dhilip",
    message: "A good friend is rare, and I’m lucky to have you in my life. Keep being your amazing self. 🫶",
    quote: "Some people enter your life and somehow make everything brighter. ❤️",
    song: {
      title: "Kongunatttu Thendraluku",
      artist: "",
      album: ""
    }
  },
  "03-11": {
    name: "Akshya P (Vennamavaley)",
    message: "I’m grateful for every laugh, every random conversation, every annoying moment and every memory we’ve made together. 🫂❤️",
    quote: "I feel so lucky and grateful to have you as my friend. 🫂✨\nYou have this beautiful way of making even the most ordinary days feel a little more special. 💖🥹\nI’m genuinely grateful for every laugh, every memory, and every moment we share. ✨\nI'm daily waiting for your message. 🫶",
    song: {
      title: "She Is a Fantasy",
      artist: "",
      album: ""
    }
  },
  "08-06": {
    name: "Rajkumar",
    message: "You’re one of those people who makes life feel a lot easier and a lot more fun. I appreciate you. 💛",
    quote: "Some people enter your life and somehow make everything brighter. ❤️",
    song: {
      title: "Kongunatttu Thendraluku",
      artist: "",
      album: ""
    }
  },
  "04-17": {
    name: "Sujan S",
    message: "It’s rare to find someone who feels like home in the middle of chaos, and you do. 🫶",
    quote: "Some friendships quietly become one of the best parts of life. 🫶",
    song: {
      title: "Jigiri Dosthu",
      artist: "Jaya Moorthy, Anthakudi Ilayaraja",
      album: "Namma Veettu Pillai"
    }
  }
};

const defaultMessage = "I'm genuinely grateful for every laugh, every random conversation, every annoying moment and every memory we've created together. 🫂❤️";

let selectedBirthday = null;
let currentSong = null;

const screens = document.querySelectorAll(".screen");
const birthMonth = document.getElementById("birthMonth");
const birthDay = document.getElementById("birthDay");
const dateError = document.getElementById("dateError");
const startBtn = document.getElementById("startBtn");
const friendName = document.getElementById("friendName");
const songTitle = document.getElementById("songTitle");
const songArtist = document.getElementById("songArtist");
const songAlbum = document.getElementById("songAlbum");
const quoteText = document.getElementById("quoteText");
const messageText = document.getElementById("messageText");
const continueBtn = document.getElementById("continueBtn");
const nextBtn = document.getElementById("nextBtn");
const playLocalBtn = document.getElementById("playLocalBtn");
const openSongBtn = document.getElementById("openSongBtn");
const localAudio = document.getElementById("localAudio");

function showScreen(id) {
  screens.forEach((screen) => screen.classList.remove("active"));
  const target = document.getElementById(id);
  if (target) {
    target.classList.add("active");
  }
}

function populateDayOptions() {
  const month = birthMonth.value;
  const selectedValue = birthDay.value;
  const daysInMonth = month ? new Date(2024, Number(month), 0).getDate() : 31;

  birthDay.innerHTML = '<option value="">Day</option>';

  for (let day = 1; day <= daysInMonth; day++) {
    const option = document.createElement("option");
    option.value = String(day).padStart(2, "0");
    option.textContent = String(day);
    if (option.value === selectedValue) option.selected = true;
    birthDay.appendChild(option);
  }
}

function formatText(value) {
  return (value || "").replace(/\n/g, "<br>");
}

function setFriendContent(friend) {
  if (!friend) return;

  friendName.textContent = friend.name;
  songTitle.textContent = friend.song?.title || "Song Title";
  songArtist.textContent = friend.song?.artist || "Artist Name";
  songAlbum.textContent = friend.song?.album || "Album Name";
  quoteText.innerHTML = formatText(friend.quote);
  messageText.innerHTML = formatText(friend.message || defaultMessage);

  currentSong = friend.song;
  if (localAudio) {
    localAudio.pause();
    localAudio.currentTime = 0;
    localAudio.removeAttribute("src");
    localAudio.load();
  }
}

function validateBirthday(month, day) {
  if (!month || !day) return false;
  const monthNumber = Number(month);
  const dayNumber = Number(day);
  const daysInMonth = new Date(2024, monthNumber, 0).getDate();
  return dayNumber >= 1 && dayNumber <= daysInMonth;
}

async function hasLocalSong() {
  return false;
}

async function handleStart() {
  const month = birthMonth.value;
  const day = birthDay.value;

  if (!validateBirthday(month, day)) {
    dateError.textContent = "Please enter a valid birthday. ❤️";
    return;
  }

  selectedBirthday = `${month}-${day}`;
  const friend = birthdayData[selectedBirthday];

  if (!friend) {
    dateError.textContent = "Looks like this surprise isn't prepared for this date yet. ❤️";
    return;
  }

  dateError.textContent = "";
  setFriendContent(friend);

  const localSongAvailable = await hasLocalSong();
  if (localSongAvailable && localAudio) {
    localAudio.src = "music/song.mp3";
    localAudio.load();
    localAudio.play().catch(() => {});
  }

  showScreen("surprise");
}

if (localAudio) {
  localAudio.removeAttribute("src");
  localAudio.load();
}

function openSongSearch() {
  if (!currentSong) return;

  const query = [currentSong.title, currentSong.artist, currentSong.album].filter(Boolean).join(" ");
  const url = `https://open.spotify.com/search/${encodeURIComponent(query)}`;
  window.open(url, "_blank", "noopener,noreferrer");
}

function toggleLocalAudio() {
  if (!localAudio || !localAudio.src) {
    openSongSearch();
    return;
  }

  if (localAudio.paused) {
    localAudio.play().catch(() => {
      openSongSearch();
    });
  } else {
    localAudio.pause();
  }
}

function createFloatingElement() {
  const element = document.createElement("div");
  element.className = "float";
  const symbols = ["❤️", "💗", "💜", "✨", "🫶", "♡"];
  element.textContent = symbols[Math.floor(Math.random() * symbols.length)];
  element.style.left = `${Math.random() * 100}vw`;
  element.style.fontSize = `${12 + Math.random() * 16}px`;
  element.style.animationDuration = `${7 + Math.random() * 8}s`;
  document.body.appendChild(element);
  setTimeout(() => element.remove(), 16000);
}

birthMonth.addEventListener("change", populateDayOptions);
startBtn.addEventListener("click", handleStart);
continueBtn.addEventListener("click", () => showScreen("memories"));
nextBtn.addEventListener("click", () => showScreen("final"));
playLocalBtn.addEventListener("click", toggleLocalAudio);
openSongBtn.addEventListener("click", openSongSearch);

populateDayOptions();
showScreen("intro");
setInterval(createFloatingElement, 900);

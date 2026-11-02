# 🎵 Music Duel

**Pick your favorite song by pointing at it.**
Music Duel is a hand-tracking music tournament. Choose a genre, then use your index finger in the air to pick the better song in every round, until only one song survives. No mouse, no keyboard — just your hand and a webcam.

Built with **Python**, **OpenCV** and **MediaPipe**.

---

## ✨ Features

- 🖐️ **Touch-free control:** point with your right index finger and hold to select.
- 🎤 **5 genres:** Rap, Rock, Pop, Jazz and Electronic, with 5 songs each.
- ⚔️ **Tournament mode:** two songs face each other, the winner stays and meets the next challenger.
- 🖼️ **Album covers:** downloaded automatically and saved for the next run.
- 🏆 **Winner screen:** shows your #1 song with simple keyboard options.
- ▶️ **YouTube shortcut:** open your winning song on YouTube with one key.

---

## 🎮 How It Works

1. **Choose a genre.** Point at a genre card and hold your finger there. A progress bar fills up, and the card is selected.
2. **Duel.** Two songs appear side by side. Hold your finger on the one you like more.
3. **Keep going.** The winning song stays and faces the next one. With 5 songs per genre, there are 4 rounds.
4. **Meet your winner.** The last song standing is your #1 song of the genre.

---

## 🕹️ Controls

| Input | Action |
|-------|--------|
| Right index finger (hold ~1.2 s) | Select a genre or a song |
| `R` | Restart the game |
| `O` | Open the winning song on YouTube (winner screen) |
| `Q` | Quit |

---

## 🧰 Requirements

- Python 3.9 – 3.12
- A webcam
- Internet connection (for the first run, to download the hand model and album covers)

Python libraries:

```
opencv-python
mediapipe
numpy
```

---

## 🚀 Getting Started

**1. Clone the repository**

```bash
git clone https://github.com/kamandNajari/Music_Duel.git
cd Music_Duel
```

**2. Install the libraries**

```bash
pip install -r requirements.txt
```

**3. Open the notebook**

```bash
jupyter notebook music_duel.ipynb
```

**4. Run the cell**

A window called **Music Duel** will open. Show your right hand to the camera and start playing!

> 💡 The hand-tracking model (`hand_landmarker.task`) is downloaded automatically the first time you run the game.

---

## 🖼️ Album Covers

Covers are downloaded in the background from the iTunes API, with Deezer as a backup, so the game never has to wait for them. Every cover is saved in the `cover_cache/` folder, so the next run is instant.

If a cover cannot be downloaded (for example, no internet or a blocked service), the game shows a colorful card with the song name and artist instead, and keeps working normally. If covers are blocked in your region, run the game once with a VPN. After that, the saved covers work without it.

---

## ⚙️ Customization

**Use your left hand.** At the top of the code, change:

```python
POINTER_HAND = "Left"
```

**Change the selection time.** Make selecting faster or slower:

```python
DWELL_SECONDS = 1.2
```

**Add your own songs or genres.** Edit the `SONGS` dictionary:

```python
SONGS = {
    "Rap": [
        {"title": "Without Me", "artist": "Eminem"},
        # add more songs here
    ],
}
```

If you add a new genre, also add a color for it in `GENRE_COLORS`.

---

## 🧠 How It Is Built

- **OpenCV** captures the webcam, mirrors the image and draws the whole interface.
- **MediaPipe Hand Landmarker** finds the hand and tracks the tip of the index finger.
- **Dwell selection:** a choice is confirmed only when the finger stays on a card long enough, which avoids accidental clicks.
- **Smoothing:** the pointer position is smoothed so the cursor moves steadily.
- **Background threads** download the covers, so the interface stays fast.

---

## 🛠️ Troubleshooting

| Problem | Solution |
|---------|----------|
| The camera does not open | Close other apps using the webcam or try `cv2.VideoCapture(1)`. |
| The pointer does not appear | Show your hand clearly in good light, and check that `POINTER_HAND` matches the hand you use. |
| Covers do not appear | Check your internet connection, or run once with a VPN. |
| The window does not close | Click on the game window and press `Q`. |

---

## 📁 Project Structure

```
Music_Duel/
├── music_duel.ipynb     # The game
├── requirements.txt     # Python libraries
├── .gitignore
└── README.md
```

---

## 📄 License

This project is licensed under the MIT License.

---

## 👩‍💻 Author

Made by **Kamand Najari**.

---

Thank you for visiting! 👾💜🎶

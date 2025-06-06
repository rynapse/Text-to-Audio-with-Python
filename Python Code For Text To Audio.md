Python Code For Text To Audio

<<<

    import tkinter as tk
    from tkinter import filedialog
    from gtts import gTTS

    def save_audio():
        text = entry.get()
        if not text:
            result_label.config(text="Please enter text.")
            return

        def on_save():
            filename = filename_entry.get()
            if not filename:
                filename_label.config(text="Enter a filename.")
                return

            folder = filedialog.askdirectory(title="Select a folder")
            if not folder:
                filename_label.config(text="No folder selected.")
                return

            try:
                tts = gTTS(text=text, lang='en')
                filepath = f"{folder}/{filename}.mp3"
                tts.save(filepath)
                result_label.config(text=f"Saved as {filename}.mp3")
                filename_window.destroy()
            except Exception as e:
                filename_label.config(text=f"Error: {str(e)}")

        filename_window = tk.Toplevel(root)
        filename_window.title("Enter File Name")
        filename_window.geometry("300x200")

        filename_entry = tk.Entry(filename_window, font=("Arial", 12))
        filename_entry.pack(pady=10)

        filename_button = tk.Button(filename_window, text="Save", command=on_save, font=("Arial", 12))
        filename_button.pack(pady=5)

        filename_label = tk.Label(filename_window, text="", font=("Arial", 10))
        filename_label.pack(pady=5)

    root = tk.Tk()
    root.title("Text to Speech")
    root.geometry("540x800")

    entry = tk.Entry(root, width=40, font=('Arial', 14))
    entry.pack(pady=20)

    convert_button = tk.Button(root, text="Convert to MP3", command=save_audio, font=('Arial', 12))
    convert_button.pack(pady=10)

    result_label = tk.Label(root, text="", font=('Arial', 12))
    result_label.pack(pady=10)

    exit_button = tk.Button(root, text="Exit", command=root.destroy, font=('Arial', 12), bg='red', fg='white')
    exit_button.place(relx=1.0, rely=1.0, anchor='se', x=-10, y=-10)

    root.mainloop()
>>>

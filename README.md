📚 [52shuku.net](https://52shuku.net/) Novel Downloader
=======================================================

A Google Colab-based script to download novels from 52shuku.net and convert them into EPUB format.

⚡ Quick Start
-------------

### 1. **Open Google Colab**

*   Go to [colab.research.google.com](https://colab.research.google.com/)
    
*   Sign in with your Google account
    
*   Click **"New Notebook"**

*   Install Required Packages if needed: The script needs pandoc and inlp. Run this code in the first cell (click the "+ Code" button, paste the code below, then click the play button):

```   
!apt-get install -y pandoc
!pip install inlp requests beautifulsoup4
```   
    

### 2. **Configure Your Book**

In the script, edit these three variables:

```   BOOK_URL = "https://www.52shuku.net/xiandaidushi/26184.html"  
    # Book's main page  BOOK_TITLE = "讨厌的赵公子"                                     
    # Book title  BOOK_AUTHOR = "Your唯"                                         
    # Author name  MAKE_EPUB = True                                               
    # True for EPUB, False for .txt
```

### 3. **Run the Script**

1.  Paste the complete script into a Colab cell
    
2.  Press **Shift + Enter** or click the play button ▶️
    
3.  Wait for completion (shows chapter download progress)
    
4.  EPUB will **auto-download** to your computer
    

📁 Output Files
---------------

*   **EPUB file** (BOOK\_TITLE.epub) – Ready for e-readers
    
*   **Text file** – If MAKE\_EPUB = False
    
*   Folder /content/tmp/ – Temporary chapter files (deleted after run)
    

🛠️ Customization Tips
----------------------

### Change Chapter Selector

If chapters aren't downloading correctly, inspect the page structure and update:

```
    # In the get_chapter() function:  
    content = soup.find('article', {'class': 'article-content', 'id': 'nr1'})
```

### Download Speed

Adjust the delay between chapter requests (in seconds):

`   time.sleep(0.5)  # Change this value (currently 0.5s)   `

⚠️ Notes
--------

*   **Respect website terms** – Use responsibly, don't overload servers
    
*   **Colab limitations** – Sessions timeout after ~90 minutes
    
*   **Chinese encoding** – Script handles Simplified/Traditional Chinese conversion via inlp (uncomment # text = chinese.s2t(text))
    
*   **EPUB metadata** – Title/author are set automatically
    

🔧 Troubleshooting
------------------

"No content found" => Check if BOOK\_URL points to the book's main page
Empty EPUB => Verify chapter links exist on the page
Encoding errors => Ensure reg.encoding = "utf-8" is present
Timeout => Re-run cell or restart runtime (Runtime → Restart runtime)

📦 Dependencies
---------------

Automatically installed:

*   requests, beautifulsoup4 – Web scraping
    
*   inlp – Chinese text conversion
    
*   pandoc – EPUB creation
    

📄 License
----------

For personal use only. Respect authors' and websites' copyrights.

**Happy reading!** 📖

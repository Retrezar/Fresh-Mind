# Fresh Mind – Weed-Related Anxiety Overcome Consulting

## 🚀 Deploy to GitHub + Vercel (Step-by-Step)

### 1. GitHub Setup
1. Go to https://github.com/new and create a repository called `fresh-mind`
2. Clone it locally:
   ```bash
   git clone https://github.com/YOUR_USERNAME/fresh-mind.git
   cd fresh-mind
   ```
3. Copy `index.html`, `001.jpg`, `002.jpg`, `fesrh_mind_logo.png` into this folder
4. Push:
   ```bash
   git add .
   git commit -m "Initial Fresh Mind website"
   git push origin main
   ```

### 2. Deploy to Vercel
1. Go to https://vercel.com → **Add New Project**
2. Import your `fresh-mind` GitHub repo
3. Click **Deploy** — Vercel auto-detects static HTML
4. Your site will be live at `https://fresh-mind.vercel.app`

---

## 🔐 Supabase Auth (Google Sign-In Setup)

### Step 1 – Create a Supabase Project
1. Go to https://supabase.com and create a free account
2. Click **New Project** → give it a name like `fresh-mind`
3. Save your **Project URL** and **anon public key**

### Step 2 – Enable Google OAuth
1. In Supabase dashboard → **Authentication → Providers → Google**
2. Enable Google provider
3. Go to https://console.cloud.google.com → Create OAuth credentials
4. Add your Vercel domain as an **Authorized Redirect URI**:
   `https://YOUR_PROJECT.supabase.co/auth/v1/callback`
5. Paste the **Client ID** and **Client Secret** into Supabase

### Step 3 – Add Supabase to Your Site
Replace the placeholder `googleSignIn()` function in `index.html` with:

```html
<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>
<script>
  const { createClient } = supabase;
  const sb = createClient('YOUR_SUPABASE_URL', 'YOUR_ANON_KEY');

  async function googleSignIn() {
    const { error } = await sb.auth.signInWithOAuth({ provider: 'google' });
    if (error) alert('Sign-in failed: ' + error.message);
  }

  async function emailSignIn() {
    const email = document.getElementById('modal-email').value;
    const password = document.getElementById('modal-pass').value;
    const { error } = await sb.auth.signInWithPassword({ email, password });
    if (error) alert(error.message);
    else { closeModal(); alert('Signed in successfully!'); }
  }
</script>
```

---

## 📁 File Structure
```
fresh-mind/
├── index.html          ← Main website
├── 001.jpg             ← Hero image
├── 002.jpg             ← About/contact image
├── fesrh_mind_logo.png ← Logo
└── README.md           ← This file
```

## 📧 Contact
- Email: freshmind@gmail.com

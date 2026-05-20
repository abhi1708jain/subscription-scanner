# Month 1 Launch Kit

This is everything you do **as a human** in Month 1. The code is done. The articles are done. This is the distribution playbook — execute it in order.

---

## Week 1: Deploy + close friends test

### Day 1-2: Deploy the new index.html

1. Open your `subscription-scanner` GitHub repo locally.
2. Replace `index.html` with the new version (the one I gave you).
3. **CRITICAL — Update three constants in the file before pushing:**
   - `EMAIL_CAPTURE_URL` — replace `YOUR_FORM_ID` with your actual Formspree URL.
     - Sign up at formspree.io (free tier = 50 submissions/month). Create a form, copy the URL.
     - Alternative: use Buttondown, ConvertKit, or n8n webhook.
   - `data-domain="findmysubscriptions.com"` in the Plausible script — confirm it matches your domain.
     - Sign up at plausible.io ($9/mo) or use Google Analytics (free).
     - If you don't want analytics yet, remove the script tag — but you'll be flying blind.
   - The `CLIENT_ID` should already be correct, but verify it matches your Google Cloud Console OAuth client.
4. In Google Cloud Console → OAuth consent screen → Scopes:
   - **Remove** `https://www.googleapis.com/auth/gmail.readonly`
   - **Add** `https://www.googleapis.com/auth/gmail.modify`
   - Add a justification: "We use gmail.modify because gmail.metadata doesn't support keyword search, and gmail.modify is classified as Sensitive (lower verification burden) compared to gmail.readonly which is Restricted. We do not modify, delete, or send any email."
5. Add yourself + 5-10 friends as **Test Users** so they can sign in before verification.
6. Commit, push, GitHub Pages auto-deploys.

### Day 3: Test it yourself

- Sign in with your own Gmail.
- Run a scan.
- Verify the amounts are roughly correct.
- Click every locked Pro feature. Check that the modal opens and emails get captured in Formspree.
- Open Plausible (or GA) and verify events are firing.

### Day 4-5: WhatsApp 20 close friends

Send this message to 20 friends individually (NOT a broadcast list — Indian WhatsApp groups treat broadcast as spam):

```
Bhai/Hey, made a small thing this weekend.
You sign in with Gmail, it finds every subscription you're paying for (Hotstar, Netflix, Cred, all of it).

Took 30 sec for me. Found ₹X/month I had no idea about 😭

Can you try it and tell me if it breaks?
https://findmysubscriptions.com
```

Personalize the first line per person. Track:
- How many open the link
- How many actually sign in
- How many message back

**Goal: 10-15 of 20 try it.** This week is about finding bugs you can't see from your own data.

### Day 6-7: Fix the bugs your friends found

There will be bugs. There will be amounts that don't extract. There will be services that don't get detected. Fix the top 3 issues. Skip the long tail.

---

## Week 2: Reddit + content seeding

### The Reddit posts (3 subreddits, posted on different days)

**Important: don't promote. Tell a story.** Reddit's anti-spam radar fires instantly. Each post is a personal story; the tool is mentioned once at the bottom as the takeaway.

### Post 1: r/IndiaInvestments (Tuesday)

**Title:** I scanned my Gmail this weekend and found ₹6,400/month of subscriptions I forgot about. Sharing what I learned.

**Body:**

> Did a weekend project — built a small tool to scan my Gmail for every subscription receipt. The results made me feel stupid.
>
> What I knew I had: Netflix, Spotify, Amazon Prime. About ₹1,500/month total.
>
> What I forgot about:
> - Hotstar Premium: kept renewing after IPL last year (₹299/month = ₹3,588/year wasted)
> - Audible India: signed up for one book, never canceled (₹199/month)
> - Cult.fit Live: lockdown leftover (₹999/month, hadn't opened the app in 14 months)
> - Times Prime: thought it was free with my credit card. It wasn't. (₹1,199/year)
> - Apple Music: forgot I had this; I use Spotify (₹99/month)
> - Adobe Creative Cloud: signed up for one freelance project (₹1,675/month)
>
> Total damage: about **₹77,000/year** I was paying without using.
>
> What I learned that might help others:
>
> 1. Bank statements don't help — merchant names like "DRI*HOTSTAR PR" are useless. Gmail receipts are way clearer.
> 2. Many Indians pay BOTH Swiggy One and Zomato Gold. Pick one.
> 3. ChatGPT Plus / Claude Pro are the new "I forgot I had this." $20 = ₹1,660/month adds up.
> 4. Annual subscriptions are sneakier than monthly ones. The big charge once a year hits when you're not paying attention.
> 5. If you have iCloud auto-upgrade on, check what tier you're actually on now.
>
> Anyway, made the tool free if anyone wants to try: [findmysubscriptions.com]. Runs in your browser, doesn't store anything. Curious what subscriptions others find when they run it — would love to hear.

### Post 2: r/personalfinanceindia (Thursday)

**Title:** Did a subscription audit. Sharing the framework + what I found.

**Body:**

> Inspired by the "subscription creep" posts here, did a full audit this weekend. Method + findings below in case useful.
>
> **Method:**
> 1. Listed every subscription I could remember from memory: 6 services, "about ₹2,000/month"
> 2. Searched Gmail manually for "receipt" and "subscription" — found 3 more I'd missed
> 3. Used a tool to automate the Gmail scan — found 4 MORE on top of those
>
> **Real total: 13 active subscriptions, ₹7,900/month, ₹94,800/year.**
>
> The 4 I never would have found manually:
> - Inshorts Prime (₹99/month — signed up during a flight, forgot)
> - Apple One Family — I thought my dad was paying, he thought I was, we were both paying separately
> - A Razorpay subscription mandate that was technically "expired" but kept retrying every month (₹499/month going to a defunct service)
> - Google One 200GB — auto-upgraded from free 15GB and I never noticed
>
> **What I did:**
> - Canceled 6 (savings: ₹4,200/month = ₹50,400/year)
> - Kept 7 that I actually use
> - Set a quarterly calendar reminder to re-audit
>
> **The math that scared me into doing this:**
> ₹4,200/month invested at 12% returns = ₹3.5 lakh in 5 years. That's a forgotten subscription tax of one car-down-payment over 5 years.
>
> Tool I used was [findmysubscriptions.com] — but honestly the manual Gmail search method works too if you have 2 hours.

### Post 3: r/NRI (Saturday)

**Title:** Fellow NRIs — you're probably paying for double the subscriptions. Did an audit.

**Body:**

> 4 years in the US. Maintain Indian credit card + US credit card. Did a subscription audit and felt like an idiot.
>
> **Indian side I was still paying for:**
> - Hotstar (parents use it — keeping)
> - JioSaavn (haven't opened in 2 years — canceling)
> - Audible India + Audible US (both active, same account spirit — canceling India)
> - Cult.fit (haven't been to India in 2 years — definitely canceling)
> - Times Prime (forgot existed)
>
> **US side I was still paying for:**
> - Spotify Premium AND Apple Music (migrated, never canceled)
> - Netflix + Hulu + Disney+ (the classic three)
> - ChatGPT Plus (use it; keeping)
> - Two iCloud subscriptions on two Apple IDs (US App Store + India App Store)
>
> Total bleed: ~$45 + ₹2,500 in waste/month. Conversion: ~$75/month, ~$900/year.
>
> Heavy NRI-specific traps I noticed:
> 1. **iCloud x 2** — if you have two Apple IDs (one US, one India), check if you're paying for storage on both.
> 2. **Amazon Prime x 2** — many NRIs keep Prime India for shipping to family. Worth it if you actively order TO them; waste if family orders themselves.
> 3. **Indian streaming services that geo-block abroad** — paying for Hotstar/SonyLIV but they don't even play in the US without a VPN.
>
> Used [findmysubscriptions.com] — free, scans both INR and USD subs together, splits totals by currency. Useful for NRIs since most US tools don't see Indian services at all.

### Reddit etiquette

- **One post per subreddit per month, MAX.** Posting daily = banned in 48 hours.
- **Reply to every comment within 12 hours.** Engagement = visibility.
- **Don't argue with critics.** Someone will say "why would I give you my Gmail." Reply once explaining read-only OAuth + browser-only. Move on.
- **If a mod removes your post,** message them politely asking what would make it compliant. Don't repost without permission.

---

## Week 3: Publish the SEO articles

You have 10 articles. Publish them in this order, one per day:

1. `cancel-hotstar.md` — highest-volume keyword
2. `cancel-netflix.md`
3. `cancel-spotify.md`
4. `cancel-jiocinema.md`
5. `cancel-cred-mint.md`
6. `cancel-swiggy-one.md`
7. `forgotten-subscriptions-india.md`
8. `find-all-subscriptions.md`
9. `nri-subscription-audit.md`
10. `stop-forgotten-charges.md`

### Where to publish

Three options, in order of preference:

**Option A (best): Your own blog at findmysubscriptions.com/blog/**

Create a `/blog/` folder in your repo. Add a simple `index.html` listing the articles. Each article becomes its own folder: `/blog/cancel-hotstar/index.html`. Convert each `.md` file to an HTML page using any markdown-to-HTML converter (pandoc, online tools, or just paste into a styled HTML template).

This gives you SEO juice on your own domain. Backlinks compound.

**Option B (good): Medium + Hashnode (cross-post)**

Post each article on both. Add a canonical link back to your domain. You get reach immediately while your own SEO ramps.

**Option C (lazy): Medium only**

Easiest. Lowest ROI. Do this only if you can't muster the energy for option A.

### Each article needs

- An SEO-friendly URL slug
- A meta description matching the TL;DR
- A clear CTA to findmysubscriptions.com (already in the articles)
- Internal links to other articles (already in the articles)

---

## Week 4: Product Hunt launch prep

**Don't launch on Product Hunt in Week 4. Prepare for it.** Launch in Week 1 of Month 2 once you have testimonials.

### What to gather this week

1. **3-5 testimonial quotes** from friends who used the tool. Ask each:
   > "If you could share one sentence about what you found using my tool, what would it be?"
2. **5 screenshots** of real scan results (with personal info blurred). Pick the most "wow"-inducing ones.
3. **A 30-second demo video.** Loom is fine. Show: open site → sign in → scan → big spending number reveal → list of subscriptions. No voiceover needed; add captions.

### Product Hunt copy to refine

**Tagline (60 chars max):** Find every subscription draining your bank account

**Description (260 chars max):**
> Scan your Gmail in 30 seconds and discover every subscription you're paying for — including the ones most tools miss like Hotstar, JioCinema, Cred, Swiggy One. Free, browser-only, nothing stored. Built by an indie dev tired of forgotten ₹999 charges.

**First comment (you post this immediately after launch):**
> Hey PH! Maker here. I built this after realizing I was paying ₹6,400/month for stuff I'd forgotten about — including a Cult.fit membership I hadn't used in 14 months.
>
> What makes this different from Rocket Money / Bobby / Truebill:
> - Works for Indian services they don't detect (Hotstar, JioCinema, Cred, Cult.fit, Swiggy One, 60+ more)
> - Works for NRIs with both INR and USD subscriptions
> - 100% browser-based — nothing stored on any server
> - Free
>
> Would love your feedback, especially: what subscription did you find that surprised you most? I'm collecting these to improve the detection.

**When to launch:** Tuesday 12:01 AM Pacific Time. PH launches reset at midnight Pacific. Tuesday-Thursday get most traffic. Avoid Monday (Asia-Pacific dominates the morning slot) and Friday (low engagement).

---

## Week 4 also: Start CASA Tier 2

This takes 4-8 weeks. If you don't start now, you'll hit the 100-user cap in Month 2 and growth stops cold.

1. Read Google's [CASA verification guide](https://developers.google.com/cloud-platform-console/casa).
2. Run [OWASP ZAP](https://www.zaproxy.org/) against your deployed site. Fix anything critical.
3. Choose an authorized lab from Google's [list](https://appdefensealliance.dev/casa) — Leviathan, Bishop Fox, Schellman, Levi9, and Orbis are common choices. Get quotes ($500-$1,500 for Tier 2).
4. Submit the SAQ (54-question security questionnaire).

If you want, I can prep the SAQ answers based on your architecture as a separate piece — it's about 4 hours of work I can save you.

---

## Tracking dashboard (set up Week 1, check daily)

Make a simple spreadsheet with these columns. Update daily.

| Week | Page views | Sign-ins | Scans completed | Emails captured | Pro modal opens | Waitlist signups |
|---|---|---|---|---|---|---|
| 1 | | | | | | |
| 2 | | | | | | |
| 3 | | | | | | |
| 4 | | | | | | |

**Targets to aim for, end of Month 1:**
- Page views: 2,000
- Sign-ins: 100-200
- Scans: 80-150
- Emails captured: 50-100
- Pro modal opens: 30-60
- Waitlist signups: 15-40

If Pro waitlist signups < 10 by end of Month 1, your conversion intent is weak — fix the Pro feature presentation before scaling traffic. If > 40, you have a real product — accelerate distribution.

---

## What NOT to do this month

- **Don't add features.** Every hour on features is an hour stolen from distribution.
- **Don't redesign.** The current design is good enough. Money comes from users, not pixels.
- **Don't build the backend.** That's Month 2.
- **Don't try paid ads yet.** You haven't validated the funnel.
- **Don't post on Twitter/LinkedIn 5x a day.** Volume kills credibility. 2x a week is the right cadence.
- **Don't respond to "what's your moat?" — there isn't one yet.** You're building one through users and content.

---

## Honest pep talk for Week 4

Month 1 will feel slow. You'll have 200 sign-ins and zero revenue and wonder if this is working. **That's exactly how Month 1 is supposed to feel.** The work is in Week 1-3; the payoff is in Month 3-5. If you quit in Month 2 because the numbers are small, you'll throw away Month 1's investment.

The math works. Trust the math. Ship the work.

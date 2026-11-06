# Add GTM + GA4 to your 5 websites

One small step at a time. Tick each box when it's done. ✅

> **The one rule:** you never paste code into the HTML pages.
> Each website has **one line** to change. Everything else happens on Google's websites.

---

## Before you start (5 min)

- [ ] Open <https://tagmanager.google.com> in one tab
- [ ] Open <https://analytics.google.com> in another tab
- [ ] Have this file open next to them

You will repeat the **same 4 parts** for each website:

```
PART A  Make a GA4 stream      -> you get   G-XXXXXXXXXX
PART B  Make a GTM container   -> you get   GTM-XXXXXXX
PART C  Paste GTM ID in code   -> 1 line in config.js
PART D  Connect GA4 inside GTM -> 2 tags, then Publish
```

💡 Do **one website completely**, then take a break, then the next one.

---

## 🧭 The 5 websites at a glance

| #   | Website             | The only file you edit                           | Line |
| --- | ------------------- | ------------------------------------------------ | ---- |
| 1   | Hospital (CareWell) | `hospital/assets/js/config.js`                   | 49   |
| 2   | Shop (ecommarce)    | `ecommarce/assets/js/config.js`                  | 66   |
| 3   | Car dealership      | `car_dealership/assets/js/config.js`             | 52   |
| 4   | Royella hotel       | `royella-luxury-hotel/assets/js/config.js`       | 65   |
| 5   | EduSpace            | `eduspace-learning-platform/assets/js/config.js` | 50   |

Every page of each site already reads this file. Change it once and all pages are covered.

---

## The 4 parts (same for every website)

### PART A - GA4: make a data stream (3 min)

- [ ] GA4 → **Admin** (gear, bottom left)
- [ ] **Create → Property** → name it after the website (e.g. `Royella Hotel`) → finish the steps
- [ ] Choose **Web** → enter the website address → **Create stream**
- [ ] Copy the **Measurement ID** (looks like `G-AB12CD34EF`)
- [ ] Write it in the table at the bottom of this file ✍️

### PART B - GTM: make a container (2 min)

- [ ] GTM → **Create Account** (first time) or **Admin → + Create Container**
- [ ] Container name = website name, target platform = **Web** → **Create**
- [ ] Close the code pop-up (**you do NOT need to copy the code**)
- [ ] Copy the ID at the top (looks like `GTM-AB1C2D3`)
- [ ] Write it in the table at the bottom ✍️

### PART C - paste the GTM ID in the code (1 min)

- [ ] Open the website's `config.js` (path + line in the table above)
- [ ] Find this line:

  ```js
  gtmContainerId: "GTM-XXXXXXX",
  ```

- [ ] Replace only the `XXXXXXX` part so it becomes your ID:

  ```js
  gtmContainerId: "GTM-AB1C2D3",
  ```

- [ ] Keep the quotes `" "` and the comma `,` ✔️
- [ ] Save the file
- [ ] ⛔ Do **not** paste the GA4 `G-` ID anywhere in the code. The `ga4MeasurementId` line below it is only a note.

### PART D - connect GA4 inside GTM (5 min)

**Tag 1 - page views**

- [ ] GTM → **Tags → New**
- [ ] Tag type: **Google tag**
- [ ] Tag ID: your `G-...` ID
- [ ] Trigger: **Initialization - All Pages**
- [ ] Name it `GA4 - Google tag` → **Save**

**Trigger - the website's events**

- [ ] GTM → **Triggers → New → Custom Event**
- [ ] Event name: paste the line from **"Event list"** for that website (below)
- [ ] Tick ☑️ **Use regex matching**
- [ ] Name it `All site events` → **Save**

**Tag 2 - events**

- [ ] GTM → **Tags → New → Google Analytics: GA4 Event**
- [ ] Measurement ID: your `G-...` ID
- [ ] Event Name: type `{{Event}}`
- [ ] Only if the website section says **🛒 shop events**: open **More settings → Ecommerce** → tick **Send Ecommerce data** → Data source **Data Layer**
- [ ] Trigger: `All site events`
- [ ] Name it `GA4 - Events` → **Save**

**Publish**

- [ ] Top right → **Submit → Publish** 🎉

---

## 1️⃣ Hospital (CareWell)

- [ ] Part A + B: name both `CareWell Hospital`
- [ ] Part C: edit `hospital/assets/js/config.js`, **line 49**
- [ ] Part D, Event list (copy all of it):

```
^(appointment_cta_clicked|appointment_form_opened|appointment_request_submitted|doctor_carousel_scrolled|doctor_profile_viewed|navigation_clicked|service_selected|site_search|video_opened)$
```

- [ ] 🛒 shop events: **no**
- [ ] Details: `hospital/ANALYTICS_GUIDE.md`

## 2️⃣ Shop (ecommarce)

- [ ] Part A + B: name both `Shop`
- [ ] Part C: edit `ecommarce/assets/js/config.js`, **line 66**
- [ ] Part D, Event list:

```
^(view_item_list|select_item|view_item|add_to_cart|remove_from_cart|view_cart|begin_checkout|size_selected|search|shop_now_clicked|navigation_clicked)$
```

- [ ] 🛒 shop events: **YES**, tick "Send Ecommerce data"
- [ ] Details: `ecommarce/ANALYTICS_GUIDE.md`

## 3️⃣ Car dealership

- [ ] Part A + B: name both `Car Dealership`
- [ ] Part C: edit `car_dealership/assets/js/config.js`, **line 52**
- [ ] Part D, Event list:

```
^(view_item_list|select_item|view_item|search|brand_filter_selected|vehicle_type_selected|filters_reset|vehicle_gallery_opened|vehicle_image_selected|vehicle_comparison_viewed|test_drive_form_opened|inquiry_validation_failed|demo_lead_submitted|generate_lead|demo_newsletter_submitted|sign_up|hero_feature_selected|content_panel_opened|language_selected|navigation_clicked|video_start)$
```

- [ ] 🛒 shop events: **YES**, tick "Send Ecommerce data"
- [ ] Details: `car_dealership/ANALYTICS_GUIDE.md`

## 4️⃣ Royella hotel

- [ ] Part A + B: name both `Royella Hotel`
- [ ] Part C: edit `royella-luxury-hotel/assets/js/config.js`, **line 65**
- [ ] Part D, Event list:

```
^(availability_search|view_item_list|select_item|view_item|begin_checkout|booking_step_completed|purchase|demo_booking_completed|dining_venue_selected|spa_treatment_selected|gallery_opened|room_filter_applied|demo_contact_submitted|generate_lead|demo_newsletter_submitted|sign_up)$
```

- [ ] 🛒 shop events: **YES**, tick "Send Ecommerce data"
- [ ] Details: `royella-luxury-hotel/ANALYTICS_GUIDE.md`

## 5️⃣ EduSpace

- [ ] Part A + B: name both `EduSpace`
- [ ] Part C: edit `eduspace-learning-platform/assets/js/config.js`, **line 50**
- [ ] Part D, Event list:

```
^(course_list_viewed|course_selected|course_enrolled|lesson_started|lesson_completed|quiz_started|quiz_submitted|quiz_completed|course_completed|search|course_category_selected|learning_dashboard_viewed|lesson_notes_saved)$
```

- [ ] 🛒 shop events: **no**
- [ ] Details: `eduspace-learning-platform/ANALYTICS_GUIDE.md`

---

## ✅ Test one website (5 min)

- [ ] GTM → **Preview** → type the website address → **Connect**
- [ ] On the website, click **Accept** on the cookie banner (otherwise nothing loads)
- [ ] Click something (e.g. a category, a course, "Check Availability")
- [ ] In the Preview window: the event appears on the left and **Tags Fired** shows `GA4 - Events`
- [ ] GA4 → **Admin → DebugView**: the same event appears within a few seconds

The website needs to be online (e.g. GitHub Pages) or running with `python3 -m http.server`.

---

## 🚫 Don't do these

| Don't | Why |
|---|---|
| Paste GTM or GA4 code into the HTML pages | The site already loads GTM, so you'd count everything twice |
| Use the same `GTM-` ID for two websites | Their data gets mixed together |
| Put the `G-` ID in `config.js` and expect it to work | The code only uses the GTM ID; GA4 lives in GTM |
| Forget **Publish** in GTM | Nothing works until you publish |
| Forget to click **Accept** while testing | The banner blocks GTM until you accept |

---

## 😵 Stuck?

| Problem | Fix |
|---|---|
| No cookie banner appears | The ID in `config.js` is still `GTM-XXXXXXX`, or it has a typo |
| Banner appears, but Preview won't connect | Click **Accept**; check the GTM ID matches the container |
| Event shows in Preview, not in GA4 | Wrong `G-` ID in Tag 2, or the container is not published |
| Shop events have no items in GA4 | Tick **Send Ecommerce data** in Tag 2 |
| Nothing at all in the console | Open DevTools → Console; each site prints its events there even without GTM |

---

## ✍️ My IDs (fill in as you go)

| Website | GTM ID | GA4 ID | Code done | GTM published | Tested |
|---|---|---|---|---|---|
| Hospital | GTM-______ | G-__________ | ☐ | ☐ | ☐ |
| Shop | GTM-______ | G-__________ | ☐ | ☐ | ☐ |
| Car dealership | GTM-______ | G-__________ | ☐ | ☐ | ☐ |
| Royella hotel | GTM-______ | G-__________ | ☐ | ☐ | ☐ |
| EduSpace | GTM-______ | G-__________ | ☐ | ☐ | ☐ |

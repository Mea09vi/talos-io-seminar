# วิธี generate ภาพประกอบ TalosTruth (ภาพเหมือนจริง)

คู่มือนี้บอกว่า **ใช้ AI เจ้าไหน**, **prompt อะไร**, และ **ตั้งชื่อไฟล์ยังไง** ให้หย่อนลงโฟลเดอร์นี้แล้วขึ้นในหน้า TalosTruth ทันที

---

## 0) หลักการสำคัญ — อย่าให้ AI เขียนตัวหนังสือ

AI สร้างภาพทุกเจ้ายัง **เขียนภาษาไทยในรูปเพี้ยน/อ่านไม่ออก** (อังกฤษพอได้ ไทยยังแย่)
→ วิธีที่ถูกต้อง: ให้ AI สร้าง **ภาพบรรยากาศ/ภาพพื้นหลังล้วน ไม่มีตัวอักษร** แล้วหน้าเว็บจะวางข้อความไทยทับให้เอง
ผลลัพธ์ = ภาพสมจริง + ตัวหนังสือไทยคมชัดถูกต้อง 100%

ดังนั้นทุก prompt ด้านล่างจะลงท้ายด้วย `no text, no watermark, no flags or insignia of real countries`

---

## 1) ใช้เจ้าไหนดี?

| เจ้า | จุดเด่น | ราคา/วิธีใช้ |
|------|--------|-------------|
| **⭐ Gemini 2.5 Flash Image ("Nano Banana")** | ทำตามคำสั่งแม่นมาก, ภาพสมจริง, แก้/รวมภาพเก่ง | **ฟรีผ่านเว็บ** [aistudio.google.com](https://aistudio.google.com) (เลือกโมเดล *Gemini 2.5 Flash Image*) · API ~$0.039/ภาพ |
| **ChatGPT (gpt-image-1 / DALL·E 3)** | ง่ายสุดถ้ามี Plus อยู่แล้ว — พิมพ์ prompt ในแชตได้เลย | ChatGPT Plus หรือ API ~$0.04–0.17/ภาพ |

**แนะนำ:** เริ่มที่ **Nano Banana บน Google AI Studio** — ใช้ฟรีผ่านเว็บ ทดลอง prompt ได้ไม่ต้องเขียนโค้ด
ถ้าคุณมี ChatGPT Plus อยู่แล้วและอยากง่ายที่สุด → วาง prompt เดียวกันในแชต ChatGPT ก็ได้ภาพเทียบเท่า

### ขั้นตอนแบบไม่ต้องเขียนโค้ด (เร็วสุด)
1. เข้า [aistudio.google.com](https://aistudio.google.com) → ล็อกอิน Google → เลือกโมเดล **Gemini 2.5 Flash Image**
2. ก๊อป prompt จากข้อ 3 ทีละอัน → กด Run → ดาวน์โหลดรูป
3. เปลี่ยนชื่อไฟล์ตามตาราง (ข้อ 2) → วางไฟล์ในโฟลเดอร์ `img/` นี้
4. รีเฟรชหน้า `truth-campaign.html` — ภาพจะขึ้นแทนพื้นหลัง gradient เอง

> ภาพแนวนอน (16:9) ทั้งหมด — ถ้าเครื่องมือให้เลือก aspect ratio ให้เลือก **16:9** (hero เลือก 21:9 ได้ถ้ามี)

---

## 2) ตั้งชื่อไฟล์ให้ตรงนี้ (สำคัญ)

วางไฟล์ `.jpg` (หรือ `.png` ก็ได้ แต่ต้องเปลี่ยนนามสกุลใน HTML) ชื่อเป๊ะตามนี้:

| ไฟล์ | ใช้ที่ | ธีม |
|------|--------|-----|
| `hero.jpg`   | แบนเนอร์หัวเว็บ | เกาะ TALOS ยามรุ่งอรุณ — ความหวัง/บ้าน |
| `fact-1.jpg` | การ์ดที่ ๑ | ครอบครัวชาวเกาะหลายรุ่น — "นี่คือบ้านเรา" |
| `fact-2.jpg` | การ์ดที่ ๒ | แผนที่เก่ายุคอาณานิคม + เส้นที่ถูกขีดด้วยไม้บรรทัด |
| `fact-3.jpg` | การ์ดที่ ๓ | เงาทหารยกพลขึ้นฝั่งยามพลบค่ำ (โทนหม่น) |
| `fact-4.jpg` | การ์ดที่ ๔ | เอกสารสนธิสัญญาเก่า + ปากกาหมึกซึม + ตราประทับ |
| `fact-5.jpg` | การ์ดที่ ๕ | แผนที่เดินเรือยุค 1980s + วงเวียนทองเหลือง |
| `fact-6.jpg` | การ์ดที่ ๖ | ห้องประชุมนานาชาติ ยกมือลงมติ (แนว UN) |
| `fact-7.jpg` | การ์ดที่ ๗ | ภาพมุมสูงท่าเรือ/สนามบินยามค่ำคืน (โทนหม่น) |

---

## 3) ชุด Prompt พร้อมใช้ (ก๊อปวางได้เลย)

> เป็นภาษาอังกฤษเพราะ AI ทำตามได้แม่นกว่า — ทุกอันออกแบบให้เข้าโทนเว็บ (น้ำเงินกรมท่า + ทอง)

**hero.jpg**
```
Cinematic wide aerial photograph of a small fictional island fishing town at golden dawn,
calm harbor with traditional wooden boats, warm sunrise light over the sea, hopeful and
peaceful mood, documentary realism, shallow haze, color grade with deep navy-blue shadows
and warm gold highlights. 21:9 wide. No text, no watermark, no flags or insignia of real countries.
```

**fact-1.jpg** — มรดก/ประชากร
```
Intimate documentary photo of a multigenerational island fishing family standing on a weathered
wooden pier at dusk, elderly grandparents and grandchildren, calloused hands, simple coastal
clothing, sense of deep roots and belonging, soft natural light, navy-and-gold color grade.
16:9. No text, no watermark, no flags or insignia of real countries.
```

**fact-2.jpg** — เส้นแบ่งยุคอาณานิคม
```
Close-up still life of an antique colonial-era nautical map on a dark wooden table, a straight
border line drawn across it with a brass ruler and dividers, a quill and old surveying instruments
beside it, dramatic low candle-like lighting, archival documentary mood, navy-and-gold tones.
16:9. No text, no watermark, no flags or insignia of real countries.
```

**fact-3.jpg** — ยึดด้วยกำลัง
```
Somber cinematic silhouette of unmarked soldiers wading ashore from landing craft onto a beach at
dusk, backlit, heavy moody atmosphere, muted desaturated palette with cold navy-blue tones, grain,
documentary war-photography style. 16:9. No text, no watermark, no flags or insignia of real countries.
```

**fact-4.jpg** — สนธิสัญญา (WL เซ็นเอง)
```
Elegant close-up of a historical bilateral treaty document on aged parchment, a fountain pen resting
on a fresh ink signature, a red wax seal and ribbon, warm desk lamp light, shallow depth of field,
official and authoritative mood, navy-and-gold color grade. 16:9. No text legible, no watermark,
no flags or insignia of real countries.
```

**fact-5.jpg** — สิทธิทางทะเล 1982
```
Vintage 1980s nautical chart of a continental shelf spread on a navigator's table, brass dividers,
parallel rulers and a compass, warm tungsten light, analog maritime documentary aesthetic, fine grain,
deep navy and gold tones. 16:9. No readable text, no watermark, no flags or insignia of real countries.
```

**fact-6.jpg** — UNSC 2847
```
Wide photograph inside a formal circular international assembly chamber, rows of delegates raising
hands to vote, solemn diplomatic atmosphere, soft overhead lighting, generic modern interior (not any
real organization), blue-and-gold institutional palette, documentary realism. 16:9. No text,
no watermark, no flags or insignia of real countries.
```

**fact-7.jpg** — การรุกราน H-45
```
High-angle night aerial photograph of a seized commercial port and small airport, runway and cranes
lit by cold floodlights, tense and ominous mood, dark navy-blue palette with sparse amber lights,
cinematic surveillance look, light haze. 16:9. No text, no watermark, no flags or insignia of real countries.
```

---

## 4) (ทางเลือก) สคริปต์ generate อัตโนมัติทั้งชุด — Gemini API

ถ้าอยากสร้างทั้ง 8 ภาพรวดเดียวด้วยโค้ด: เอา API key จาก [aistudio.google.com](https://aistudio.google.com) (ฟรี) แล้วรัน

```bash
pip install google-genai pillow
set GEMINI_API_KEY=คีย์ของคุณ      # PowerShell: $env:GEMINI_API_KEY="คีย์ของคุณ"
python generate_images.py
```

ไฟล์ `generate_images.py` (วางในโฟลเดอร์ `img/` นี้):

```python
import os
from google import genai
from google.genai import types

client = genai.Client(api_key=os.environ["GEMINI_API_KEY"])
MODEL = "gemini-2.5-flash-image"

PROMPTS = {
    "hero":   "Cinematic wide aerial photo of a small fictional island fishing town at golden dawn, calm harbor, hopeful peaceful mood, documentary realism, navy-blue shadows and warm gold highlights. No text, no watermark, no real flags or insignia.",
    "fact-1": "Documentary photo of a multigenerational island fishing family on a weathered pier at dusk, deep roots and belonging, soft light, navy-and-gold grade. No text, no watermark, no real flags or insignia.",
    "fact-2": "Antique colonial nautical map on dark wood, a straight border drawn with a brass ruler and dividers, quill and surveying tools, dramatic low light, archival mood, navy-and-gold. No text, no watermark, no real flags or insignia.",
    "fact-3": "Somber silhouette of unmarked soldiers wading ashore from landing craft at dusk, backlit, muted cold navy palette, grain, documentary war photography. No text, no watermark, no real flags or insignia.",
    "fact-4": "Close-up of a historical treaty on aged parchment, fountain pen on a fresh signature, red wax seal, warm lamp light, official mood, navy-and-gold. No readable text, no watermark, no real flags or insignia.",
    "fact-5": "Vintage 1980s continental-shelf nautical chart on a navigator's table, brass dividers and compass, warm tungsten light, analog maritime aesthetic, navy and gold. No readable text, no watermark, no real flags or insignia.",
    "fact-6": "Wide photo inside a formal circular international assembly chamber, delegates raising hands to vote, solemn diplomatic mood, generic interior, blue-and-gold palette, realism. No text, no watermark, no real flags or insignia.",
    "fact-7": "High-angle night aerial of a seized port and small airport lit by cold floodlights, tense ominous mood, dark navy palette with amber lights, cinematic. No text, no watermark, no real flags or insignia.",
}

for name, prompt in PROMPTS.items():
    print("generating", name, "...")
    resp = client.models.generate_content(
        model=MODEL,
        contents=prompt,
        config=types.GenerateContentConfig(response_modalities=["IMAGE"]),
    )
    for part in resp.candidates[0].content.parts:
        if part.inline_data:
            open(f"{name}.jpg", "wb").write(part.inline_data.data)
            print("  saved", f"{name}.jpg")
```

> หมายเหตุ: ชื่อพารามิเตอร์/โมเดลของ SDK อาจปรับตามเวอร์ชัน — ถ้า error ให้ดูตัวอย่างล่าสุดที่หน้า AI Studio (ปุ่ม **Get code**)

---

## 5) เคล็ดลับคุณภาพ
- อยากได้หลายแบบ → กด Run ซ้ำ แล้วเลือกอันที่ชอบ (แต่ละครั้งไม่เหมือนกัน)
- โทนไม่เข้าเว็บ → เติมท้าย prompt: `muted, desaturated, deep navy blue and gold color grade`
- คนหน้าเพี้ยน/มือเพี้ยน → เปลี่ยนเป็นมุมไกลขึ้นหรือเป็นเงา (silhouette) จะเนียนกว่า
- ไฟล์ใหญ่เกิน → ย่อเป็น JPG กว้าง ~1600px ก่อนวาง (เว็บโหลดเร็วขึ้น)

*สถานการณ์ฝึกสมมุติ — ภาพทั้งหมดเป็นภาพประกอบเพื่อการฝึกเท่านั้น*

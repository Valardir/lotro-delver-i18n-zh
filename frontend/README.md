# Simplified Chinese (zh): translation guide

Lotro Delver is a fan-made database and toolbox website for the MMO The Lord of the Rings Online (LOTRO):
- item, quest, skill and effect databases
- character builds and a build generator
- instance guides and maps
- community guides and news

The readers are Chinese LOTRO players who use the community Chinese client pack. Write for them.

## Language and tone

- **Simplified Chinese** (zh-Hans, mainland conventions).
- Address the reader as **你**, never 您. Keep it friendly and concise, like a modern gaming site.
- Translate the meaning, not word by word: a button stays short, and a help text reads naturally.
- Interface wording follows common Chinese web conventions: 登录, 注册, 退出登录, 设置, 保存, 取消, 删除, 编辑, 搜索,
  筛选, 排序, 加载中…, 复制链接, 分享.

## Game terms: the client pack decides

The Chinese client pack (`client_local_ZH.dat`) already translates the game. Every game term must read exactly as the
pack has it: names of places, NPCs, monsters, items, classes, races, stats, skills, traits, deeds, currencies and
game mechanics. Look them up in the export's `LotroDescriptions.db` (`StringTables` and `StringTemplates`, columns
`text_en` / `text_zh`), and prefer the most frequent rendering. Only when the pack has no reference do you make your
own translation, consistent with the pack's style.

### Cleaning up pack strings

Pack strings sometimes carry client markup. Never copy it:
- grammar tags like `[e]`, `[m]`, `[f]`
- `\q`
- `${0x...}` tokens
- a trailing `(English)` the pack leaves in brackets: "瑞文戴尔（Rivendell）" becomes 瑞文戴尔
- `DNT -` prefixes

## Fixed glossary (use these everywhere)

### Game terms, from the pack

| English | 中文 |
|---|---|
| Deed / Deeds | 事迹 |
| Quest | 任务 |
| Instance | 副本 |
| Skirmish | 对战 |
| Raid | 团队副本 |
| Trait / Traits | 特性 |
| Trait Tree | 特性树 |
| Specialization | 专精 |
| Virtue | 美德 |
| Legendary Item | 传奇物品 |
| Essence | 精华 |
| Item set | 套装 |
| Set bonus | 套装加成 |
| Item level | 物品等级 |
| Morale | 士气 |
| Fate | 信念 (as the pack's stat table; other stat names too, e.g. 战斗中士气回复, 治疗输出等级) |
| Wit (virtue) | 才智 |
| Power | 能量 |
| Stats | 属性 (individual stats: look them up, e.g. Critical Rating 暴击等级) |
| Effect | 效果 |
| Skill | 技能 |
| Class | 职业 |
| Race | 种族 |
| Level | 等级 |
| Outfit / Cosmetic | 外观 |
| Wardrobe | 衣柜 |
| Barter | 兑换 |
| Kinship | 家族 |
| Fellowship (the in-game group) | 护戒队 (as the pack) |
| Reputation | 声望 |
| Crafting | 制作 |
| Recipe | 配方 |
| Title | 称号 |
| Mount | 坐骑 |
| Monster Play | 怪物扮演 |
| Session Play | 剧情扮演 |
| Mastery | 精通 |
| Finesse | 策略 |
| Character | 角色 |
| Equipment | 装备 |
| Inventory | 背包 |
| Vault | 库房 |
| Housing | 房屋 |
| Region | 地区 |
| Map | 地图 |
| Collections | 收藏 |
| Hope / Dread | 希望 / 恐惧 |
| Instance difficulty tier | 难度 |
| Gold / Silver / Copper (coins) | 金币 / 银币 / 铜币 |
| Item | 物品 |
| Monster | 怪物 |

### Site terms (fixed by the lead)

| English | 中文 |
|---|---|
| Lotro Delver | Lotro Delver (never translated) |
| The Lord of the Rings Online | 《指环王 Online》 (as the pack) |
| NPC / NPCs | NPC |
| Tome / Tomes | 典籍 |
| LOTRO | LOTRO |
| Build (a character build) | 配装 |
| Build Generator | 配装生成器 |
| Guide | 攻略 |
| Spotlight | 精选 |
| News | 新闻 |
| Member / Members | 会员 |
| Early access | 抢先体验 |
| Tier (the site's membership or reward tiers) | 等阶 |
| Roster | 角色名单 |
| Account | 账户 |
| Dashboard / Overview | 概览 |
| Bug Hub | 问题中心 |
| Get involved | 参与贡献 |
| Support (help desk) | 支持 |
| Changelog | 更新日志 |

## Typography

- **Full-width punctuation** in Chinese text: ，。：；！？（）, and quotes as “ ”.
- **No spaces** between Chinese characters, and none between Chinese and numbers or placeholders.
- **One space** between a Chinese character and a Latin letter: 用 AI 翻译, 原始 JSON, PvMP 军阶.
- **Keep "…"** as in English (加载中…). A sentence ends with 。, except short labels and buttons, which have no full
  stop.
- **Keep the English** for keyboard keys, file formats (JSON, PNG, MP4), code, URLs, product names (Discord,
  Google, Patreon) and unit symbols.

## Placeholders and structure

**Structure**
- Keep every key, and the same nesting and list lengths. Translate only the values.
- Copy every placeholder exactly: `{name}`, `{0}`, `${PLACEHOLDER}`, `%s`, `%d`, `<rgb=…>…</rgb>`, HTML or
  markdown tags, and markdown link URLs `](…)`.
- Keep `\n` line breaks as they are.

**Placeholder order**
- `{name}` and `{0}` may move within the sentence.
- `${PLACEHOLDER}` and `%s` are filled in order, so keep their order the same as in English.

**Plurals**
- Frontend: sibling keys like `…_one` / `…_other` or `…One` / `…Many`. Chinese has one form, so give each sibling
  the same Chinese text.
- Backend: plural *objects* `{"one": …, "other": …}`. Give `{"other": "…"}` only.

**When English is kept**
- A string with no words to translate, such as "×{0}", "JSON" or a URL, stays as English has it.

## Backend `guide.json` and `effect_mechanics.json`

These are sentence pieces that the code joins in a fixed order.
- Translate each piece so that the joined result reads acceptably in Chinese.
- Joiners: `text.sep`, `and`, `or` and `list` become `、`, `和`, `或`, with no spaces around them.
- The number format: `,` for thousands, `.` for decimals, and no space before `%`.
- Where the English word order makes good Chinese impossible, translate as well as you can and note the key as

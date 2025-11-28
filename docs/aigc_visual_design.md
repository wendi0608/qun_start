# AIGC 视觉设计工作流

本指南提供了从需求分析到高质量视觉内容生成的标准流程，确保输出符合品牌调性与目标场景。

## 1. 需求分析清单
- **业务目标**：上线位置、转化目标（曝光/点击/注册/购买）。
- **人群画像**：年龄、性别、地域、消费偏好、使用场景（App/小程序/线下屏幕）。
- **品牌调性**：主色/辅助色、字体、构图与留白、情绪关键词（沉稳/活力/科技/温暖等）。
- **物料约束**：Logo/ICON、必备文案、禁止元素、尺寸与分辨率、导出格式。
- **竞争参考**：参考链接、不可模仿的品牌、差异化方向。

## 2. 提示词（Prompt）设计原则
1) **结构化**：使用「主题 + 主体 + 场景 + 构图 + 光效 + 质感 + 色彩 + 风格 + 镜头」的固定骨架。
2) **品牌一致性**：显式写入品牌色值、字体特征、Logo 位置指示（如“左上角 15% 留白”）。
3) **场景适配**：根据终端（移动端/桌面/户外屏）调整纵横比与细节复杂度；交互场景需突出可点元素、按钮留白。
4) **可控性**：列出必须包含的物体与禁止元素；必要时加入“flat illustration/realistic render/3D clay style”等明确风格标签。
5) **多版本探索**：默认生成 4-8 张，使用批量提示词微调色彩、光线和构图（示例见下）。

### 通用提示词骨架
```
<主题>，<主体描述>，出现在<场景>，<构图与机位>，<光照>，<色彩与材质>，<风格/笔触>，高分辨率，细节清晰，品牌色 <#HEX>，Logo 预留<位置与比例>，纵横比 <宽:高>
```

### 禁止元素（Negative Prompt）
- 违禁：侵权品牌元素、烟酒、裸露、暴力、政治敏感内容。
- 质量：多余手指/肢体、文字拼写错误、畸形透视、严重噪点、低分辨率。
- 风格：与品牌冲突的配色或过度纹理（如科技品牌避免复古颗粒）。

## 3. 品牌调性模板
- **科技/专业**：冷色系（#0052FF/#0A1F44），硬朗光影，几何构图，金属/玻璃材质，关键词「科技感」「信赖」「精准」。
- **生活/温暖**：暖色系（#FF7A45/#F2C94C），柔和光源，浅景深，真实质感或手绘纹理，关键词「亲和」「舒适」「日常」。
- **潮流/活力**：高饱和撞色（#FF4D4F/#22D3EE），广角或鱼眼，霓虹光效，渐变背景，关键词「活力」「张力」「动感」。

## 4. 生成流程
1. **收敛需求**：根据第 1 节清单完成问卷，确认输出尺寸与交付格式。
2. **编写提示词**：用骨架填入主题/场景/品牌元素，补充禁止元素列表。
3. **多版本生成**：
   - 通过批量提示词调整色彩与构图（例：冷/暖光、俯视/平视、左/右构图）。
   - 控制种子或随机性，保证可复现与多样性并存。
4. **评估与筛选**：
   - 结构：主体清晰、视觉层级分明、文字位置留足。
   - 品牌：色值、Logo 留白、字体风格符合规范。
   - 适配：在目标尺寸模拟（移动端/横屏/竖屏）中检查可读性。
5. **微调**：对入选图使用 Inpainting/Outpainting 修补细节，必要时二次提示词加强纹理或光影。
6. **导出与交付**：输出 WebP/PNG/SVG，附带提示词、参数（模型、步数、CFG、种子），方便复现。

## 5. 示例提示词
- **科技金融 App Banner（横版 1920x540）**
  - 正向：
    > Fintech banner, futuristic city skyline made of glass circuits, a young professional looking at holographic financial dashboards, wide-angle, center composition with leading lines, cool blue palette #0A1F44 and cyan accent #22D3EE, glossy metal and glass texture, cinematic rim light, ultra-detailed, brand logo reserved top-left 15% blank, aspect ratio 16:9.
  - 负向：
    > low quality, blurry, extra limbs, distorted hands, wrong text, low resolution, vintage grain, warm retro tone.

- **母婴品牌海报（竖版 1080x1920）**
  - 正向：
    > Soft nursery room at sunrise, young mother holding baby with gentle smile, close-up portrait, shallow depth of field, warm pastel palette #FFB6C1 and cream #FFF6E5, cotton texture, soft rim light, hand-drawn illustration feeling, logo reserved bottom-right 12% blank, aspect ratio 9:16.
  - 负向：
    > harsh shadows, cold neon lights, metal texture, extra fingers, creepy expressions, text artifacts.

- **潮流运动鞋 KV（1:1）**
  - 正向：
    > Trendy sneakers floating with neon trails, graffiti wall background, dynamic diagonal composition, high saturation magenta #FF4D4F and teal #22D3EE, glossy rubber and mesh texture, dramatic studio lighting, particle effects, square format 1:1, logo reserved center-bottom 10% blank.
  - 负向：
    > muted colors, dull lighting, excessive grain, retro sepia, low detail, distorted shoes.

## 6. 交付清单模板
- 生成图片：PNG/WebP/SVG（注明分辨率与色域）。
- 提示词：正向、负向、生成参数（模型/步数/CFG/种子/尺寸/采样器）。
- 版本记录：每轮迭代的差异点与选中理由。
- 品牌校验：色值与 Logo 位置截图、可读性检查。

## 7. 与团队协作的快捷方式
- 将提示词拆分为片段，可在设计/产品/品牌侧快速替换（如颜色、场景、主体）。
- 针对常见终端预设纵横比：1:1、16:9、9:16、4:5，并在提示词中明确。
- 为运营位预留文字安全区（20%-30% 顶部或底部留白），在提示词中写明。
- 维护提示词库与优秀案例库，定期基于转化指标复盘并优化模板。

通过以上流程，可以根据品牌与场景快速生成高适配度的 AIGC 视觉方案，并保持可复现与一致性。

## 8. 模型与工具选择建议
- **生成模型**：
  - 写实/产品：SDXL、SD 3、Midjourney Niji 6（注意授权）。
  - 插画/潮流：Midjourney V6、Flux Dev/Realism。
  - 轻量/实时：本地 SD Turbo/LCM，适合快速迭代草图。
- **调参默认值**：CFG 5-7，步数 20-35，Sampler DPM++ 2M Karras；针对低频纹理可用 Euler a；人像可适当提高步数与面部修复。
- **辅助插件**：ControlNet（姿态/深度/草图约束）、IP-Adapter（风格参考）、InstantID（人像一致性）、LoRA（品牌物料风格化）。
- **素材版权**：确认素材来源与授权范围，避免使用受限图库或侵权元素；对外交付时附上授权说明。

## 9. 常见场景尺寸与提示词快速填充
| 场景 | 尺寸/比例 | 关键提示词 | 留白要求 |
| --- | --- | --- | --- |
| App 首页 Banner | 1080x540（2:1） | 「中心构图」「品牌色」「高对比按钮区域」 | 底部 25% 文字安全区 |
| App 详情 KV | 1080x1080（1:1） | 「主体放大」「浅景深」「产品高亮」 | 下方 20% 文案区 |
| 开屏/全屏广告 | 1080x1920（9:16） | 「纵深感」「人像视线对镜头」「右侧光源」 | 中间 30% 保留按钮区 |
| H5 封面/长图 | 1242x2208（9:16） | 「分层构图」「渐变背景」「顶部标题突出」 | 顶部 20% 标题区、底部 20% CTA 区 |
| 桌面官网 Hero | 1920x900（16:9） | 「宽幅景深」「左图右文」「柔和光」 | 右侧 40% 文字与按钮区 |

## 10. 质量自检与交付复现清单
1. **构图可读性**：主体占画面 40%-60%，层级分明，CTA 区域清晰。
2. **品牌一致性**：色值误差 < 3%，Logo 留白满足规范，字体或笔触风格统一。
3. **细节检查**：无多余肢体/错字/畸变；玻璃、金属、织物等材质纹理符合预期。
4. **跨尺寸适配**：在目标尺寸与备用尺寸上检查裁切与可读性（如 1:1/16:9/9:16）。
5. **可复现性**：保存提示词、模型版本、步骤、CFG、种子、采样器、控制图与参考图；对入选方案备注选用理由。

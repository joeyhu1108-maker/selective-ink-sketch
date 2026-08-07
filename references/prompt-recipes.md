# 图像编辑 Prompt 配方

把源照片标记为唯一 `edit target`。不要把风格参考图附在运行时输入中；风格规则已由本 Skill 编码。

黄金样例只用于生成前检查取舍、完成度断层、墨色比例和空白功能，不得作为第二张运行时图片，也不得把样例题材写进无关照片的 Prompt。

## 共同骨架

```text
Use case: style-transfer
Asset type: standalone observational pen-and-ink sketch
Input image: Image 1 is the sole edit target and factual source.
Primary request: Redraw the source photograph as an original selective monochrome pen-and-ink observation sketch. Interpret rather than mechanically trace.
Source lock: Preserve the subject count, recognizable silhouette, proportions, pose or architectural geometry, camera direction, crop, and identity-bearing features.
Selection plan: Keep [must keep]. Simplify [secondary]. Omit [clutter]. Remove roughly [density target] of low-value photographic information.
Medium: near-black hand-drawn pen lines on clean warm-white or natural-white paper; light construction lines, broken descriptive lines, and a few heavier structural accents.
Hierarchy: one dominant density anchor at [anchor], no more than two secondary anchors, quiet paper elsewhere.
Focus rendering: Treat [anchor] as the only locally completed zone. Use [ink-mass / directional-hatching / corrective-overdraw] as the dominant method. Let completion fall rapidly from focused rendering to basic description to structural hints or blank paper.
Shading: sparse directional hatching only at contact, overlap, structural recess, or identity-bearing shadow.
Output: the finished sketch alone, matching the source orientation. No hand, sketchbook, spiral binding, desk, scene photograph, frame, mockup, or process view.
Avoid: photo filter, edge detection, vector outline, uniform stroke width, coloring-book line art, pencil, charcoal, watercolor, grayscale wash, gradient shading, random scribble texture, invented details, fake text, signature, date, seal, or watermark.
```

## 局部刻画插件

根据主体与焦点只选择一个版本加入 Prompt：

```text
Ink-mass focus: Build the focal darks from a few irregular connected near-black shapes at true recesses, contacts, or overlaps. Keep dry gaps and broken edges inside the dark cluster. Do not turn the whole subject into a silhouette.
```

```text
Directional-hatching focus: Develop only the focal plane with hand-drawn parallel strokes that follow its surface direction. Allow uneven spacing, mismatched starts and stops, and rapid thinning away from the anchor. All other planes stay mostly blank.
```

```text
Corrective-overdraw focus: Preserve a few searching contours, overshoots, and 1–3 structural correction lines only around the focal junction. Thicken the true overlap after the correction, while adjacent edges remain incomplete.
```

三种版本都追加：

```text
Completion contrast: The focal zone may be carefully observed, but adjacent regions must visibly drop to basic lines, skeleton marks, lost edges, or untouched paper. No watercolor wash, diluted ink wash, airbrushed gray, or smooth gradient tone. Any middle value must come from visible pen-line spacing.
```

## 破型插件

默认使用 `controlled`；只有动态强烈或用户明确要求破型时使用 `strong`：

```text
Controlled form breaking: Select 2–4 true overlaps, structural turns, or pressure points. Break the closed contour there through unequal gaps, a few searching overshoots, small black-white cuts, and slightly offset restarts. Preserve recognition, anatomy, subject count, and structural logic.
```

```text
Strong form breaking: Leave roughly 30–45% of non-critical outer contours open. Along the true action or perspective direction, use decisive segments, gaps, penetrating search lines, offset restarts, and irregular dark knots with white cuts. Let the eye reconstruct the form from fragments. Broken form must not create duplicate limbs, facial features, roofs, windows, or invented anatomy.
```

两种版本都遵守：

```text
Form-breaking discipline: Break closure, not structure. Keep at least one unmistakable recognition anchor and all essential joints or load-bearing relationships. Avoid random scribble, mechanical motion halos, smooth filled silhouettes, and evenly damaged edges around the whole subject.
```

## Architecture 插件

```text
Architecture mode: Lock the horizon and vanishing directions first. Preserve the building profile, regional structural language, roof/eave or facade rhythm, and one recognition-bearing feature. Concentrate detail at the selected tower, gate, arch, facade junction, or street terminus. Leave sky and broad wall planes mostly blank. Suggest repeated windows, tiles, bricks, and foliage instead of drawing every unit. Remove incidental crowds, vehicles, wires, clouds, and unreadable signage unless one is essential for scale or identity.
```

## Figure 插件

```text
Figure mode: Lock the line of action, weight distribution, shoulder-hip relation, supporting foot, silhouette, and identity-bearing accessories. Keep clothing surfaces mostly blank; draw folds only at joints, compression, tension, and overlap. Simplify hands and feet without changing anatomy or finger count. Remove the background except for one grounding line when needed.
```

动态人物追加：

```text
Gesture-rhythm lock: Preserve the source's primary action curve through shoulders, torso, pelvis, and the main extended or supporting leg. Preserve one counter-curve formed by the arm, garment hem, or opposite leg, plus the recognizable negative shapes between arm and torso and between the legs. Perspective exaggeration may strengthen near-far scale, but must not replace these curves with a stiff low-angle stance, heroic pose, jump, or kick. Priority: gesture rhythm first, form breaking second, perspective exaggeration third, detail last.
```

## Landscape 插件

```text
Landscape mode: Lock the source landform profile, horizon, dominant slope or shoreline direction, scale relationship, and one recognition-bearing natural structure. Make [selected peak / rock buttress / tree convergence / shoreline turn] the sole high-completion anchor. Describe only a few major gullies, strata, trunks, wave breaks, or glacier seams there; let all surrounding terrain fall rapidly to broken skeleton marks and untouched paper. Treat sky, snow, cloud, fog, water glare, and quiet ground as paper rather than filled tone. Clouds and fog should interrupt and erase contours instead of being enclosed by cloud outlines. Use visible directional pen hatching only on the selected structural plane, with rapid thinning away from the anchor. Keep any tiny person or building as a compact secondary scale marker. Use a broken foreground baseline with sparse irregular contacts, never a continuous dark band or uniform texture field.
```

雪山、云雾或高反差自然景观追加：

```text
Atmospheric blank-space lock: Let unmarked paper perform the bright snow, sky, and obscuring mist. Mountain edges may stop inside white, disappear for long intervals, and restart slightly offset. Do not replace atmospheric omission with gray wash, soft gradients, blurred shading, or complete cloud contours. Concentrate the deepest black in no more than 1–3 true rock recesses plus an optional tiny scale figure.
```

## 植物插件

```text
Plant treatment: Draw growth axes, trunks, branches, or petiole directions first. Sample only a few leaves at turns, overlaps, and outer edges. Organize crowns as broken clusters with internal white holes. Concentrate dark ink only at one selected convergence, branch crossing, or root contact; reduce secondary plants to a few incomplete gestures. Do not draw every leaf or fill sky, water, distant mountains, or ground with wash.
```

## Portrait 插件

```text
Portrait mode: Preserve facial geometry, age, expression, asymmetry, hairline, and the most identity-bearing anchor, which may be eyes, eyewear, hair, hat, closed-eye expression, or mouth shape. Use sparse broken lines on skin, loose circling or crossing lines for hair, and a few heavier accents at jaw, eyewear, hair overlap, or the hand near the face. Do not beautify or complete every facial edge.
```

## 密度替换

- `loose`: 删除约 55%–70% 的信息；只保留结构骨架、身份锚点和极少量阴影。
- `standard`: 删除约 40%–60% 的信息；默认使用。
- `dense`: 删除约 25%–40% 的信息；细节集中在焦点，其他区域仍保持空白。

## Field note 插件

仅在用户提供精确文字时添加：

```text
Field note: Add the exact text "[verbatim user text]" in a small informal handwritten note at the lower corner. Do not invent, alter, stylize into a copied signature, or add any other text.
```

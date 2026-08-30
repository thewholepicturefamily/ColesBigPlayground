# Art prompts for Cole's Big Playground

Everything learned about generating images for this game, so a new chat can write
prompts that work first time instead of the twelfth.

Melissa generates in Gemini on an iPad and sends the results back as jpegs. She
does not want a single house style across the whole game: each area is a
different toy material, as if the game were made from different toy bins.

## The prompt shape that works

Always this order, one paragraph, no line breaks:

1. **Frame line**, now FIRST, ahead of everything:
   `Square image with a pure white background, nothing else in the frame.`
   It used to sit mid-prompt and Gemini sometimes ignored it (a wide spade on a
   pale blue background). Front-loaded, it holds.
2. **Style line**, unchanged every time:
   `Cute flat cartoon children's game illustration, thick clean outlines, soft
   bright colours, simple rounded shapes, friendly and warm, no text, no
   watermark.`
3. **Framing line**, unchanged every time:
   `Single object centred, drawn bold and simple so it still reads clearly at
   the size of a thumbnail.`
4. **Bridging block** (see below) whenever the material has realistic texture.
5. **Material sentence.** Name the material AND what its surface does. This is
   the sentence that decides whether it comes back painted or flat.
6. **Object description.** Say the viewing angle, then the parts, then anything
   that must NOT be there.
7. **Red line last**, if the game tints it (see "One red version").

## The bridging block

Discovered in the sandbox batch: this paragraph blends realistic texture into
the cartoon style instead of letting the image drift photographic. Paste it
between the framing line and the material sentence, word for word:

`The whole illustration stays in the cartoon style: thick dark outlines, simple
rounded shapes, and flat soft colour shading. The realistic texture is painted
on top of that cartoon base as fine hand-drawn surface detail inside the
outlines, small repeated marks, speckles and grain lines drawn in slightly
lighter and darker tones of the object's own colour. The texture never becomes
photographic: no photo textures, no 3D rendering, no realistic lighting, no
camera depth of field. It should look like a cartoon sticker of the material,
not a photograph of it.`

Why it works: "painted on top of that cartoon base" gives an order of
operations, "inside the outlines" protects the cutout, "tones of the object's
own colour" keeps texture shading safe for the red-recolour pipeline, and
"cartoon sticker of the material" is the anchor image. Proven on sand, ribbon
and painted wood; water came back good with it too.

## The rule that took twelve tries to learn

Name the surface, not the material. Gemini renders flat vector unless it has
texture detail to draw.

- Works: clay with `gentle fingerprint dents and a slightly rough handmade edge`
- Works: metal construction toy with `a row of evenly spaced holes down each
  plate, slotted screw heads and nuts at every joint`
- Works: silicone with `a fine even matte grain, crisp mould lines where parts
  meet`
- Works: pressed damp sand with `a fine even grainy speckle across every
  surface, soft crisp moulded edges`
- Works: pleated fabric ribbon with `fine visible weave lines, crisp folded
  pleats, clean stitched edges`
- Works: painted wood with `faint wood grain lines showing through the paint,
  soft visible brush strokes, gently rounded sanded edges`
- Works: glossy liquid water with `one large soft curved window highlight, thin
  rounded ripple lines inside, a slightly darker tone along the bottom edge`
- Fails: "glossy moulded plastic", "made of foam", "soft rubber". Smooth
  materials give it nothing to draw and it falls back to flat vector.

Other hard-won points:

- **Do not say "well-loved", "scuffs", "dents", "worn".** It reads as dirty.
  Say `clean and new` and list the wear words as negatives.
- **Do not chase photo realism.** Words like "photographed", "studio lighting",
  "3D asset", "claymation" produce a photo or a render, which cannot be cut out
  and does not match the drawn children.
- **Spot photo drift by the outline.** When two generations disagree, the one
  with the thick dark outline is the game one. A thin or coloured outline and
  soft airbrushed shading means it drifted; reject it (this is how the water
  drop pair was judged).
- **Reference images:** attach at most two, and they must be from the same
  generation as each other, or Gemini blends two styles and produces neither.
  The cheese and the sandwich are the reliable pair. Open with
  `Match the rendering style of the attached images exactly: the same painted
  finish, the same soft shading and gradients, the same outline weight and
  colour. Both attached images are from the same set and match each other.
  Match the rendering, not the material and not the colours.`
- **Same object, new material:** to remake an existing game character in a
  different material (the pet snail as a stone prize), attach just that one
  image and open with `Keep the exact same [object] as the attached image: the
  same shape, the same pose, the same proportions, the same outline weight and
  cartoon style. Change only the material, the surface texture and the colour
  as described.` Know the trade: the reference's rendering tends to win over
  the new material sentence (the stone snail came back glossy like the pet, not
  granite). Fine when likeness matters more than material.
- **Gemini may fill containers.** The sand bucket came back with a sand fill
  despite "empty". If empty truly matters, say `the open top shows only the
  inside wall, no sand surface`. Sometimes the fill looks better; judge per
  image.
- **Text-only prompts work fine** when the material sentence is good. The whole
  Fix-It Shed set and all five sandbox toys were generated with no references.
- **One red version, then recolour.** Anything the game tints (letter blocks,
  gems, backpack prizes) is generated once in `bright cherry red with only
  lighter red highlights, a soft darker red shadow, and the dark outline. No
  other colours anywhere on it`. The pipeline hue-rotates it into the seven
  game colours.
- Ask for two generations of anything fiddly or any first-time material, and
  keep the better one.
- Never describe a scene with several objects. Every scene attempt failed;
  single objects always work.

## Materials by area

| Area | Material | Surface words that work |
| --- | --- | --- |
| Snack Shack | soft modelling clay | fingerprint dents, rough handmade edge |
| Sandbox treasure (gems, coin) | soft modelling clay | same as above |
| Sandbox toys | pressed damp sand | fine even grainy speckle, soft crisp moulded edges |
| Fix-It Shed | screw-together metal construction toy | plate holes, slotted screws, nuts, plastic gears |
| Splash Pad | thick soft silicone bath toy | fine even matte grain, crisp mould lines |
| Build Zone | painted wood | deliberately left as it is, do not convert |
| Playground | none | grass, sky and children, no material needed |

Backpack prizes are each in the material of the thing they picture, not one
shared bin: water drop in glossy water, badge in pleated ribbon, play doh pot
in clay, snail in the pet snail's own rendering, sign in painted wood.

## Done

Foods (22), sandbox gems and coin, fish tank, snail garden, four wooden blocks,
all six children from behind, Tristan building, splash pad bucket, jet base,
rainbow, letter block, the whole Fix-It Shed set (four robot moods, dial,
spanner), all five sandbox toys in pressed damp sand (`sand_mound`,
`sand_spade`, `sand_bucket`, `sand_sieve`, `sand_rock`), and all five backpack
prizes in red (`prize_drop` glossy water, `prize_badge` ribbon rosette,
`prize_playdoh` kept as its original image, `prize_snail` from the pet snail,
`prize_sign` painted wood signpost).

## Still to do

Nothing. The art list is complete. New art only if the game grows.

## After the images come back

Melissa sends jpegs. The build pipeline (`pipeline.zip`) has
`browser/cutout.py` to remove the background and size them, and
`browser/embed.py` to splice them into the game. Watch for enclosed white areas
(the inside of a bucket, a donut hole) which need clearing separately.

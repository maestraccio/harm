# harm
### Harm: A Counter-Traditional Harmonizing Program

"Harmonies" are conventionally defined in Western Classical Music theory
(abbreviated as WCM) as "simultaneously sounding tones in a harmonious manner".
This definition raises at least two questions: What exactly constitutes a
"tone," and what qualifies as "harmoniously"?

#### 1. Tone:
Sound is defined as the "audible movement of air." A "tone", in contrast,
refers to "sound at a measurable frequency". For practical reasons, "harm" will
utilize the commonly accepted twelve-semitone/chromatic evenly divided (or
"well tempered") scale to define and label twelve distinct notes within each
octave (referred to here as a "block of twelve semitones"), with each higher
octave having double the frequency of the lower one. The notes are identified
using the seven letters of WCM, with sharps for the in-between semitones: [A,
A♯, B, C, C♯, D, D♯, E, F, F♯, G, G♯]. This naming convention is arbitrary. To
minimize confusion, every "black key" is always considered a "white key with a
sharp", and every "white key" consistently retains the same letter. While this
naming method is still being explored, it provides a necessary starting point.

#### 2. Harmony:
The concept of what is considered "harmoniously" is influenced by tradition,
culture, and personal taste, while also being rooted in natural harmonics.
Different musical styles may perceive various combinations as more consonant
than others. For instance, in BeBop-Jazz, a "plain tonic triad" might be viewed
as dissonant, whereas a certain degree of "WCM dissonance" could be considered
consonant within that genre. WCM harmonies are distinctly named and typically
include the same tones, aside from octaves.  The fundamental aspect of a
"harmony" consists of a set of "consonants", tones that closely align with the
lower overtones in air-carried sounds, such as the "perfect fifth" (third
overtone) and the "major third" (fifth overtone). It is important to note that
the second and fourth overtones are octaves of the fundamental, resulting in
[1, (2,) 3, (4,) 5], which is identified as "tonic" or "root". For example, in
the combination \<c e g\>, \<c\> serves as the fundamental, \<e\> represents the
fifth overtone transposed two octaves down, and \<g\> is the third overtone
transposed one octave down. Any other combinations of tones (or situations
where octaving transforms one or more consonants into dissonants) are perceived
as less consonant/tonic in WCM due to the natural laws governing sound
transmission through air.

#### BUT:
What if these overtones were not consonant? For example, if they were carried
through a medium other than air, such as a different gas or liquid?  Consider a
straight stick partially submerged in water; the part below the surface appears
different from the portion above. This analogy can also apply to sound.
Different tone combinations could be perceived as consonant, while the
traditional "tonic" chord might be deemed dissonant. This concept inspired the
idea of breaking free from the constraints of nature and creating new harmonies
using the twelve available tones, defined by user-inputted consonant/dissonant
criteria, while still adhering to the same — yet adaptable — composing rules.

In the new program "harm", users must be able to perform the following actions
at a minimum:

- Insert a "Melody": Users can input a melody either manually through a text
  prompt or by importing it from a file. The melody should include at least one
  note and a time signature, with Lilypond syntax recommended.
- Set "Melody As Bass Line": Use the melody not as the highest voice but as the 
  lowest. All other voices go on top of the melody instead of below.
- Set the "Scale": Traditionally, WCM scales consist of seven tones, with some
  exceptions. In "harm", users can choose between three to twelve tones to
  create a scale that repeats in every octave, similar to WCM. The term "scale"
  will be used instead of "tonality".
- Set "Levels of Consonance and Dissonance": Users will specify which intervals
  in the scale are considered consonant (stable: no tendency to resolve) and
  which are deemed dissonant (unstable: tendency to resolve). WCM recognizes
  four levels: perfect consonance, imperfect consonance, dissonance, and strong
  dissonance. A single note is never classified as dissonant; however, a
  distance of "0" between two separate voices (known as "perfect unison") can
  be categorized as such by the user through this setting. Fewer levels may be
  more appropriate for simpler scales, while more levels may be suitable for
  complex scales.
- Set "Dissonant Resolutions": In WCM, one of the tones in a dissonant interval
  typically resolves downward into an imperfectly consonant interval. "harm"
  users must decide whether a dissonant note should resolve upwards or
  downwards into another interval, or not, and indicate whether that interval
  is or may be consonant or dissonant and at which level.
- Set "Leading Tones Allowance": Set a minimum/maximum of "Leading Tones": Use
  a tone that is outside the selected scale to resolve by a half-step to a
  scale tone, upwards, downwards, or both.
- Set the "Jump": Users can define how far a single voice is allowed to jump up
  or down (crossing more than one scale tone) and whether it can transition to
  a consonant or dissonant interval (and to what level) from either a consonant
  or dissonant interval. The voice must obviously remain within its defined
  range.
- Set the "Voice Crossing Allowance": Users can specify whether voices are
  permitted to cross each other or if their ranges are constrained by
  surrounding voices.
- Set the "Dissonance Level Range": Set between which minimum and
  maximum the dissonance of the harmonies may and must be.
- Set the "Endpoint Dissonance Level": Users can determine how dissonant a
  resolution can be for it to be considered an "endpoint". This is essential
  when achieving full consonance is not feasible due to a higher "vertical
  rate" or an excessive number of assigned dissonants.
- Set the "Vertical Rate": This refers to how many voices are sounding
  simultaneously, which can impact the overall level of dissonance unless a
  higher "interval parallels allowance" is established.
- Set the "Range" of Each Voice: This setting is necessary to prevent all
  voices from becoming overly cluttered together.
- Set the "Interval Parallels Allowance": In WCM, the use of "perfect octave"
  and "perfect fifth" parallels is generally discouraged, and "dissonant"
  parallels are considered problematic. Users can specify which parallels are
  allowed or forbidden.
- Set the "Horizontal Rate": This setting determines how many changes are
  permitted or mandatory per time unit. The time unit is defined by the melody
  provided by the user (or potentially by "mel" in the future). The "mandatory"
  setting governs continuous harmonic movement if the melody tone remains
  unchanged. In "Choral mode", the harmony is adjusted only with each change in
  the melody tone.
- Set the "Note Repetition": Set if a non-changing note is repeated in the next
  harmony, is tied, is a Rest (if allowed), or based on "Rate of Simultaneous
  Movements".
- Set the "Rest Allowance": Define if every voice should always play a note, or
  if and how many rests are allowed.
- Set the "Rate of Simultaneous Movements": The minimum value is "1", allowing
  only one tone to transition to a new tone (with dissonants taking precedence
  over consonants, based on their level of dissonance). The maximum value is
  "0", where all voices can move at the same time. This value must never exceed
  the "vertical rate".
- Set the "Transpose Rate": This setting specifies whether — and to what extent
  — the entire tonal environment can shift to a different "fundamental". This
  adjustment may be necessary if the provided melody includes tonal elements
  not represented by the chosen scale, and it can also enhance the harmonic
  outcome. Options may include allowing movement to a "perfect consonant"
  (which is the most common approach in WCM), or any other scale tone — whether
  consonant or dissonant — or any other tone, or none at all.
- Set the "Start and Endpoint": Define if the first and/or last harmony should
  have a predefined bass note, stucture, or not.
- Set "Bass Line Exceptions": Define specific rules for the lowest voice, like
  "Drone" for one tone only for the whole melody or until an endpoint is
  reached, "Jumpy" for extra movement, "Walking", etc.

The program must facilitate the input of a melody along with its time unit
using basic Lilypond syntax. It should generate a harmonic "accompaniment" in
straightforward Lilypond syntax for PDF score and MIDI file output, while also
issuing relevant error and warning messages when certain actions cannot be
performed. Furthermore, it should provide all possible results, and the option
to combine portions of different calculations.

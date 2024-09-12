# harm
### Harm: A Counter-Traditional Harmonizing Program
"Harmonies" are conventionally defined in Western Classical Music theory (here
abbreviated as WCM) as "simultaneously sounding tones in a harmonious manner".
This definition raises at least two questions: What exactly constitutes a
"tone," and what qualifies as "harmoniously"?

#### 1. Tone:
Sound is defined as the "audible movement of air". A "tone", in contrast,
refers to "sound at a measurable frequency". For practical reasons, "harm" will
utilize the commonly accepted twelve-semitone/chromatic evenly divided (or
"well tempered") scale to define and label twelve distinct notes within each
octave (referred to here as a "block of twelve semitones"), with each higher
octave having double the frequency of the lower one. The notes are identified
using the seven letters of WCM, with sharps for the in-between semitones: [A,
Ais, B, C, Cis, D, Dis, E, F, Fis, G, Gis]. This naming convention is
arbitrary. To minimize confusion, every "black key" is always considered a
"white key with a sharp", and every "white key" consistently retains the same
letter. While this naming method is still being explored, it provides a
necessary starting point. While the word "Tone" indicates the actual sound, the
word "Note" is used for the representation of that tone, either on paper or in
the programming code.

#### 2. Harmony:
The concept of what is considered "harmoniously" is influenced by tradition,
culture, and personal taste, while also being rooted in natural harmonics.
Different musical styles may perceive various combinations as more consonant
than others. For instance, in BeBop-Jazz, a "plain tonic triad" might be viewed
as dissonant, whereas a certain degree of "WCM dissonance" could be considered
consonant within that genre. WCM harmonies are distinctly named and typically
include the same notes, aside from octavings. The fundamental aspect of a
"harmony" consists of a set of "consonants", tones that closely align with the
lower overtones in air-carried sounds, such as the "perfect fifth" (third
overtone) and the "major third" (fifth overtone). It is important to note that
the second and fourth overtones are octaves of the fundamental, resulting in
[1, (2,) 3, (4,) 5], which is identified as "tonic" or "root". For example, in
the combination \<c e g\>, \<c\> serves as the fundamental, \<e\> represents
the fifth overtone transposed two octaves down, and \<g\> is the third overtone
transposed one octave down. Any other combinations of tones (or situations
where octaving transforms one or more consonants into dissonants) are perceived
as less consonant/tonic in WCM due to the natural laws governing sound
transmission through air.

#### BUT:
What if these overtones were not consonant? For example, if they were carried
through a medium other than air, such as a different gas or liquid? Consider a
straight stick partially submerged in water; the part below the surface appears
different from the portion above. This analogy can also apply to sound.
Different tone combinations could be perceived as consonant, while the
traditional "tonic" chord might be deemed dissonant. This concept inspired the
idea of breaking free from the constraints of nature and creating new harmonies
using the twelve available tones, defined by user-inputted consonant/dissonant
criteria, while still adhering to the same — yet adaptable — composing rules.

In the new program "harm", users must be able to perform the following actions
at a minimum:

#### Base Material:
- Insert a "Melody": Users can input a single melody line with a time signature
  and at least one note, in Lilypond absolute syntax, like
  \{\\time 3/4 a'4 b'8 cis''8 d''4 f''2.\}
  - manually through a text prompt
  - by importing it from a file
  
- Set the "Vertical Rate": This refers to how many voices are playing
  simultaneously. Voices are referred to as "Voice" rather than "Instrument",
  "Line" or "Staff" (or any other terminology).
- Set the "Volunteer": Assign this role to one or more voices, to step outside
  an "Endpoint" and initiate a new sequence from a new dissonant harmony, after
  the "Endpoint Skip Horizontal Rate".
- Set the "Voice Crossing Allowance": Users can specify whether voices are
  permitted to cross each other or if their ranges are constrained by
  surrounding voices.
- Set "Melody As Other Voice": Use the melody not as the highest voice but as
  another voice of choice. All other voices go around or on top of the melody
  instead of below.
- Set the "Repetition Rate": Prevent repeated equal movements, for instance if
  the "Volunteer" initiates a dissonant harmony that they resolve themselves,
  after which they are assumed to move to another dissonant again.

#### Tonal Environment:
- Set the "Scale and Fundamental": Traditionally, WCM scales consist of seven
  notes, with some exceptions. In "harm", users can choose between three to
  twelve notes to create a scale that repeats in every octave, similar to WCM.
  The term "scale" will be used instead of "tonality". The scale does not need
  to contain only melody notes if a "Transpose Rate" is set, otherwise at some
  point an error will be raised. The choice of a "Fundamental" is optional.
- Set "Levels of Consonance and Dissonance": Users will specify which intervals
  in the scale are considered consonant (stable: no tendency to resolve) and
  which are deemed dissonant (unstable: tendency to resolve). WCM recognizes
  four levels: perfect consonance, imperfect consonance, dissonance, and strong
  dissonance. A single note is never classified as dissonant; however, a
  distance of "0" between two separate voices (known as "perfect unison") can
  be categorized as such by the user through this setting. Fewer levels may be
  more appropriate for simpler scales, while more levels may be suitable for
  complex scales. Possible consonant/dissonant extensions may include
  "mandatory" and "prohibited".
- Set the "Dissonance Level Range": Set between which minimum and maximum the
  dissonance of the harmonies must stay. Minimum dissonance equals maximum
  consonance. Takes into account the "Levels of Consonance and Dissonance".
- Set the "Endpoint Dissonance Level": Users can determine how dissonant a
  resolution can be for it to be considered an "endpoint". Takes into account
  the "Levels of Consonance and Dissonance".
- Set the "Transpose Rate": This setting specifies whether — and to what extent
  — the entire tonal environment can shift to a different scale with the same
  structure. This adjustment may be necessary if the provided melody includes
  notes that are not represented by the chosen scale, and it can also enhance
  the harmonic outcome. Options may include allowing movement up or down with a
  "perfect consonant" interval (which is the most common approach in WCM), or
  any other scale note — whether consonant or dissonant — or any other note, or
  none at all. The Transposision Rate is entered as an interval up or down.
- Set the "Horizontal Rate": This setting determines how many changes are
  permitted or mandatory per time unit. The time unit is defined by the user
  provided Lilypond fragment (or potentially by "mel" in the future). The
  "mandatory" setting governs continuous harmonic movement if the melody note
  remains unchanged. In "Choral mode", the harmony is adjusted only with each
  change in the melody note.
- Set the "Endpoint Skip Horizontal Rate": When a (consonant) "Endpoint" is
  reached, wait longer before the next change, initiated by the "Volunteer".
- Set the "Start and Endpoint": Define if the first and/or last harmony should
  have a predefined bass note, stucture, or not. If set, to the affected
  voice(s), a starting and/or an ending note must be assigned in absolute
  Lilypond syntax. If "Voice Crossing Allowance" is "OFF" and given notes are
  crossing, a relevant error should be raised.

#### Single-voice Variables:
- Set the "Range" of each voice: This setting is necessary to prevent all
  voices from becoming overly cluttered together.
- Set the "Jump": Users can define how far a single voice is allowed to jump up
  or down (crossing more than one scale note) and whether it can transition to
  a consonant or dissonant interval (and to what level) from either a consonant
  or dissonant interval. The voice must obviously remain within its defined
  range.
- Set "Leading Tones Allowance": Set a minimum/maximum of "Leading Tones": Use
  a note that is outside the selected scale to resolve by a half-step to a
  scale note, upwards, downwards, or both.
- Set the "Note Repetition": Set if a non-changing note is repeated in the next
  harmony, is tied, is a Rest (if allowed), or influenced by the "Rate of
  Simultaneous Movements".
- Set the "Rest Allowance": Define if a voice should always play a note, or if
  and how many rests are allowed.
- Set "Voice Exceptions": Define specific exceptions for a specific voice, like
  "Drone" for one note only for the whole melody or until an endpoint is
  reached, "Jumpy" for extra movement, "Walking", etc. where for every
  exception set specific variables can be defined. Applies in WCM mostly to the
  lowest (bass) voice, but can in "harm" be assigned to any voice. Suggested
  names are being evaluated.

#### Multi-voice Variables:
- Set "Dissonant Resolutions": In WCM, one of the notes in a dissonant interval
  typically resolves downward into an imperfectly consonant interval. "harm"
  users must decide whether a dissonant note should resolve upwards or
  downwards into another interval, or not, and indicate whether that interval
  is or may be consonant or dissonant and to which level. This setting leads
  primarily the generation of the next harmony, other variables/restrictions
  are considered later on in this process.
- Set the "Interval Parallels Allowance": In WCM, the use of "perfect octave"
  and "perfect fifth" parallels is generally discouraged, and "dissonant"
  parallels are considered problematic. Users can specify which parallels are
  allowed or forbidden.
- Set the "Rate of Simultaneous Movements": The minimum value is "1", allowing
  only one note to transition to a new note, with dissonants taking precedence
  over consonants, based on their dissonance level. The maximum value is "0",
  where all voices can move at the same time. This value must never exceed the
  "vertical rate".

The program must facilitate the input of a melody along with its time unit
using basic Lilypond syntax. It should generate a harmonic "accompaniment" in
straightforward Lilypond syntax for PDF score and MIDI file output, while also
issuing relevant error and warning messages when certain actions cannot be
performed. Furthermore, it should provide all possible results, and the option
to combine portions of different calculations.

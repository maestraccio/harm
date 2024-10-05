<h1>harm</h1>
<h3>Harm: A Counter-Traditional Harmonizing Program</h3>
"Harmonies" are conventionally defined in Western Classical Music theory (here
abbreviated as WCM) as "simultaneously sounding tones in a harmonious manner".
This definition raises at least two questions: What exactly constitutes a
"tone," and what qualifies as "harmoniously"?

<h3>1. Tone:</h3>
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
the programming code. As "harm" will not produce sound, the term "note" is used
here.

<h3>2. Harmony:</h3>
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
the combination &lt;c e g&gt;, &lt;c&gt; serves as the fundamental, &lt;e&gt;
represents the fifth overtone transposed two octaves down, and &lt;g&gt; is the
third overtone transposed one octave down. Any other combinations of tones (or
situations where octaving transforms one or more consonants into dissonants)
are perceived as less consonant/tonic in WCM due to the natural laws governing
sound transmission through air.

<h3>BUT:</h3>
What if these overtones were not consonant? For example, if they were carried
through a medium other than air, such as a different gas or liquid? Consider a
straight stick partially submerged in water; the part below the surface appears
different from the portion above. This analogy can also apply to sound.
Different tone combinations could be perceived as consonant, while the
traditional "tonic" chord might be deemed dissonant. This concept inspired the
idea of breaking free from the constraints of nature and creating new harmonies
using the twelve available tones, defined by user-inputted consonant/dissonant
criteria, while still adhering to the same — yet adaptable — composing rules.

<h2>In the new program "harm", users must be able to perform the following actions at a minimum:</h2>

<h3>Base Material:</h3>
<ul>
  <li>
    Insert a "Melody": Users can input a single melody line with a time
    signature and at least one note and one ore more optional "Endpoint"
    markings, in Lilypond absolute syntax, like<br>
    <code>{\time 3/4 a'4 b'8 cis''8 d''4 \bar "." f''2.}</code><br>
    where every extra <code>\bar "."</code> or doubled bar line indicates an
    "Endpoint". After an "Endpoint", all voices are a "one-time volunteer",
    where a completely new harmony is set up, to initiate a new sequence after
    the "Endpoint Skip Horizontal Rate", like initiating a new melody.
    <ul>
      <li>
        manually through a text prompt
      </li>
      <li>
        by importing it from a .ly-file. Only the first melody statement is
        used and it may contain only single notes: no chords
        <code><...></code> and no polyphony
        <code><<{...}\\{...}>></code>.
      </li>
    </ul>
  </li>
  <li>
    Set the "Vertical Rate": This refers to how many voices are playing
    simultaneously. Voices are referred to as "Voice" rather than "Instrument",
    "Line" or "Staff" (or any other terminology).
    <ul>
      <li>
        as a number, including the given melody, if the melody is one of the
        voices in the total ensemble (see also "Melody as Other Voice" and
        "Protagonist")
      </li>
      <li>
        as a preset ensemble, like "ViVaVc String Trio" or "SATB Choir", with
        predefined settings, like voice range and "Rest Allowance".
      </li>
    </ul>
  </li>
  <li>
    Set the "Volunteer": Assign this role to one or more voices, to step
    outside a consonant harmony and initiate a new sequence from a new harmony.
    Assign exceptional options to 
    <ul>
      <li>
        Move to a dissonant instead of a consonant, to different dissonance
        levels:
        <ul>
          <li>
            "Yes"
          </li>
          <li>
            "No"
          </li>
        </ul>
      </li>
      <li>
        Set a different "Jump", in order to always facilitate a new starting
        point:
        <ul>
          <li>
            Only next scale note
          </li>
          <li>
            Jump to other scale note
          </li>
          <li>
            Jump to "Leading Tone"
          </li>
          <li>
            Jump to any note, only if "Transpose Rate" is set
          </li>
        </ul>
      </li>
      <li>
        Allow moving down instead of up:
        <ul>
          <li>
            "Yes"
          </li>
          <li>
            "No"
          </li>
        </ul>
      </li>
      <li>
        Allow moving up instead of down:
        <ul>
          <li>
            "Yes"
          </li>
          <li>
            "No"
          </li>
        </ul>
      </li>
    </ul>
  </li>
  <li>
    Set "Melody As Other Voice": Use the melody not as the highest voice but as
    another voice of choice, as part of the ensemble. All other voices go
    around or on top of the melody instead of below.
    <ul>
      <li>
        Choose one other voice to assign the melody to
        <ul>
          <li>
            Octaving option to fit in voice range
          </li>
        </ul>
      </li>
    </ul>
  </li>
  <li>
    Set "Protagonist": if the melody voice stands out as a soloist and does not
    take part in de ensemble that form the harmony. If this option is chosen,
    the "Protagonist" can also be silent for the duration of the "melody"
    ("tacet al fine" in WCM), to create a random series of harmonies, yet
    following the settings.
  </li>
  <li>
    Set the "Voice Crossing Allowance": Users can specify whether voices are
    permitted to cross each other or if their ranges are constrained by
    surrounding voices.
    <ul>
      <li>
        "Yes"
      </li>
      <li>
        "No"
      </li>
    </ul>
  </li>
  <li>
    Set the "Repetition Rate": Prevent repeated equal movements, for instance
    if the "Volunteer" initiates a dissonant harmony that they resolve
    themselves, after which they are assumed to move to another dissonant
    again.
    <ul>
      <li>
        "Off": The "Volunteer" can move back to the same previous dissonant and
        perform the same resolution again, over and over, until the melody
        moves and forces a different decision.
      </li>
      <li>
        "On": Set a number of maximum repetitions before the "Volunteer" must
        decide on another dissonant to move to.
      </li>
    </ul>
  </li>
</ul>

<h3>Tonal Environment:</h3>
<ul>
  <li>
    Set the "Scale and Fundamental": Traditionally, WCM scales consist of seven
    notes, with some exceptions. In "harm", users can choose between three to
    twelve notes to create a scale that repeats in every octave, similar to WCM.
    The term "Scale" will be used instead of "tonality" or any other term. The
    "Scale" does not need to contain only melody notes if a "Transpose Rate" or
    "Leading Tones Allowance" is set, otherwise at some point an error will be
    raised. The choice of a "Fundamental" is optional.
    <ul>
      <li>
        Choose three to twelve notes in a one-octave range (from twelve semitones),
        which are to be considered the "Scale".
      </li>
      <li>
        Optionally choose a "Fundamental", to define a bass note with a
        corresponding consonant harmony for "Endpoint". The "Fundamental" will
        follow the "Transpose Rate", if set.
      </li>
    </ul>
  </li>
  <li>
    Set "Levels of Consonance and Dissonance": Users will specify which intervals
    in the scale are considered consonant (stable: no tendency to resolve) and
    which are deemed dissonant (unstable: tendency to resolve). WCM recognizes
    four levels: perfect consonance, imperfect consonance, dissonance, and strong
    dissonance. A single note is never classified as dissonant; however, a
    distance of "0" between two separate voices (known as "perfect unison") can
    be categorized as such by the user through this setting. Fewer levels may be
    more appropriate for simpler scales, while more levels may be suitable for
    complex scales. Available levels are:
    <ul>
      <li>
        Mandatory: Must be present in every harmony
      </li>
      <li>
        Perfect Consonant: Will be the last to change, unless in the voice assigned
        as "Volunteer"
      </li>
      <li>
        (Imperfect) Consonant: Has no active tendency to move, unless in the voice
        assigned as "Volunteer"
      </li>
      <li>
        (Mild) Dissonant: Has a tendency to move
      </li>
      <li>
        Strong Dissonant: Has a strong tendency to move and will be the first to
        change
      </li>
      <li>
        Prohibited: Is forbidden in every harmony
      </li>
    </ul>
    Any note outside the scale is considered dissonant and can only be used if
    <ul>
      <li>
        A "Transpose Rate" is set
      </li>
      <li>
        "Leading Tones Allowance" is set
      </li>
    </ul>
    or at least any one of the above
  </li>
  <li>
    Set the "Dissonance Level Range": Set between which minimum and maximum the
    dissonance of the harmonies must stay. Minimum dissonance equals maximum
    consonance. Takes into account the "Levels of Consonance and Dissonance".
  </li>
  <li>
    Set the "Endpoint Dissonance Level": Users can determine how dissonant a
    resolution can be for it to be considered an "endpoint". Takes into account
    the "Levels of Consonance and Dissonance".
  </li>
  <li>
    Set the "Transpose Rate": This setting specifies whether the entire tonal
    environment can shift to a different scale with the same structure. This
    option may be necessary if the provided melody includes notes that are not
    represented by the chosen scale and their movement cannot be solved with
    "Leading Tones Allowance". It can also just enrich the harmonic outcome.
    Options may include
    <ul>
      <li>
        to a "perfect consonant" interval (which is the most common approach in
        WCM) from the first "Scale" only. The last "Scale" to use must equal the
        first, so if used, it must also go back again.
      </li>
      <li>
        to one or more chosen scale note(s)
        <ul>
          <li>
            from the first "Scale" only
          </li>
          <li>
            set a maximum number of levels
          </li>
          <li>
            set if the last "Scale" to use must equal the first
          </li>
        </ul>
      </li>
      <li>
        to any note, even outside the "Scale"
        <ul>
          <li>
            from the first "Scale" only
          </li>
          <li>
            set a maximum number of levels
          </li>
          <li>
            set if the last "Scale" to use must equal the first
          </li>
        </ul>
      </li>
      <li>
        none at all
      </li>
    </ul>
    The "Transpose Rate" is entered as an interval up or down.
  </li>
  <li>
    Set the "Horizontal Rate": This setting determines how many changes are
    permitted or mandatory per time unit. The time unit is defined by the user
    provided Lilypond fragment (or potentially by "mel" in the future). The
    "mandatory" setting governs continuous harmonic movement if the melody note
    remains unchanged. In "Choral mode", the harmony is adjusted only with each
    change in the melody note.
    <ul>
      <li>
        "1 Per Beat": Set a mandatory change on every beat, indicated by the
        lower time signature number.
      </li>
      <li>
        "1 Per Measure": Set a mandatory change on every measure, indicated by
        the lower time signature number multiplied by the upper.
      </li>
      <li>
        "Every # Beats": Set a mandatory change on every "# Beats", indicated
        by the lower time signature number multiplied by a user inputted
        number.
      </li>
    </ul>
    If more changes per beat are wanted, change the time signature of the
    melody accordingly.
  </li>
  <li>
    Set the "Endpoint Skip Horizontal Rate": When a (consonant) "Endpoint" is
    reached, wait longer before the next change, initiated by the "Volunteer".
    <ul>
      <li>
        "# Beats": Set a number of beats, indicated by the lower time signature
        number.
      </li>
    </ul>
  </li>
  <li>
    Set the "Start and Endpoint": Define if the first and/or last harmony should
    have a predefined bass note, stucture, or not. If set, to the affected
    voice(s), a starting and/or an ending note must be assigned in absolute
    Lilypond syntax. If "Voice Crossing Allowance" is "OFF" and given notes are
    crossing, a relevant error should be raised.
    <ul>
      <li>
        "Start Harmony Dissonance": Set how dissonant a starting harmony must
        be.
      </li>
      <li>
        "Starting Harmony": Set an absolute starting harmony by defining every
        starting note for each voice.
      </li>
      <li>
        "Start Bass Note": Set only on which bass note the sequence must start.
      </li>
      <li>
        "End Harmony Dissonance": Set how dissonant an ending harmony must be.
      </li>
      <li>
        "Ending Harmony": Set an absolute ending harmony by defining every
        ending note for each voice.
      </li>
      <li>
        "End Bass Note": Set only on which bass note the sequence must end.
      </li>
    </ul>
  </li>
</ul>

<h3>Single-voice Variables:</h3>

<ul>
  <li>
    Set the "Voice Range" of each voice: This setting is useful to prevent all
    voices from becoming overly cluttered together. It can be set to "Unlimited"
    to override.
    <ul>
      <li>
        "Individually": Choose a lowest and highest note for every individual
        voice. The individual voices can be sorted/stacked manually.
      </li>
      <li>
        "Preset": All voices have predefined ranges taken from the selected
        "Preset Ensemble", or can be selected individually but immutable from a
        drop-down list with traditional instruments.
      </li>
      <li>
        "Unlimited": All voices have unlimited ranges.
      </li>
    </ul>
  </li>
  <li>
    Set the "Jump": Users can define how far a single voice is allowed to jump 
    up or down (crossing more than one scale note) and whether it can transition
    to a consonant or dissonant interval (and to what level) from either a
    consonant or dissonant interval. The voice must obviously remain within its
    defined range. It is entered as an inclusive allowance.
    <ul>
      <li>
        "Up": Defines the allowed jumps to a higher note
        <ul>
          <li>
            "{_defined-dissonance-or-consonance-level-here_}":
            <ul>
              <li>
                "Yes": Set max interval
              </li>
              <li>
                "No"
              </li>
            </ul>
          </li>
          <li>
            "{_defined-dissonance-or-consonance-level-here_}":
            <ul>
              <li>
                "Yes": Set max interval
              </li>
              <li>
                "No"
              </li>
            </ul>
          </li>
        </ul>
        "Down": Defines the allowed jump to a lower note
        <ul>
          <li>
            "{_defined-dissonance-or-consonance-level-here_}":
            <ul>
              <li>
                "Yes": Set max interval
              </li>
              <li>
                "No"
              </li>
            </ul>
          </li>
          <li>
            "{_defined-dissonance-or-consonance-level-here_}":
            <ul>
              <li>
                "Yes": Set max interval
              </li>
              <li>
                "No"
              </li>
            </ul>
          </li>
        </ul>
      </li>
    </ul>
  </li>
  <li>
    Set "Leading Tones Allowance": Set a minimum/maximum of "Leading Tones": Use
    a note that is outside the selected scale to resolve by a half-step to a
    scale note, upwards, downwards, or both.
    <ul>
      <li>
        "Lead Up":
        <ul>
          <li>
            "Yes":
            <ul>
              <li>
                "Horizontal Number": Set max number of optional occurrences per voice.
              </li>
              <li>
                "Vertical Number": Set max number of optional parallel
                occurrences over multiple voices. This number can never exceed
                the maximum number of voices.
              </li>
            </ul>
          </li>
          <li>
            "No"
          </li>
        </ul>
      </li>
      <li>
        "Lead Down":
        <ul>
          <li>
            "Yes":
            <ul>
              <li>
                "Horizontal Number": Set max number of optional occurrences per voice.
              </li>
              <li>
                "Vertical Number": Set max number of optional parallel
                occurrences over multiple voices. This number can never exceed
                the maximum number of voices.
              </li>
            </ul>
          </li>
          <li>
            "No"
          </li>
        </ul>
      </li>
    </ul>
  </li>
  <li>
    Set the "Note Repetition": Set if a non-changing note is
    repeated/played/struck in the next harmony, is tied, is a Rest (if allowed),
    or influenced by the "Rate of Simultaneous Movements".
    <ul>
      <li>
        "Tie": Hold the note as long as possible
      </li>
      <li>
        "Repeat": Play the note again in every new harmony where it occurs
      </li>
      <li>
        "Rest": Don't play the note again but "play" one rest instead.
      </li>
    </ul>
  </li>
  <li>
    Set the "Rest Allowance": Define if a voice should always play a note, or if
    and how many rests are allowed.
    <ul>
      <li>
        "Yes":
        <ul>
          <li>
            "Max Horizontal Number": Set after how many rests a note must be
            played
          </li>
          <li>
            "Max Vertical Number": Set how many voices can "play" a rest at the
            same time
          </li>
        </ul>
        "After Rest": Set what type of note must be played after a rest:
        <ul>
          <li>
            "Step Up": Choose a note one step higher than the last played note
            <ul>
              <li>
                "{_defined-dissonance-or-consonance-level-here_}"
              </li>
            </ul>
          </li>
          <li>
            "Jump Up": Choose a note one jump higher than the last played note.
            This can also be a step.
            <ul>
              <li>
                "{_defined-dissonance-or-consonance-level-here_}"
              </li>
            </ul>
          </li>
          <li>
            "Step Down": Choose a note one step lower than the last played note
            <ul>
              <li>
                "{_defined-dissonance-or-consonance-level-here_}"
              </li>
            </ul>
          </li>
          <li>
            "Jump Down": Choose a note one jump lower than the last played
            note. This can also be a step.
            <ul>
              <li>
                "{_defined-dissonance-or-consonance-level-here_}"
              </li>
            </ul>
          </li>
        </ul>
      </li>
      <li>
        "No"
      </li>
    </ul>
  </li>
  <li>
    Set "Voice Exceptions": Define specific exceptions for a specific voice, like
    "Drone" for one note only for the whole melody or until an endpoint is
    reached, "Jumpy" for extra movement, "Walking", etc. where for every
    exception set specific variables can be defined. Applies in WCM mostly to the
    lowest (bass) voice, but can in "harm" be assigned to any voice. Suggested
    names are being evaluated.
    <ul>
      <li>
        Assign a special rule to one or more voices:
        <ul>
          <li>
            "Drone": Play only one note throughout the melody until an
            "Endpoint" is reached
          </li>
          <li>
            "Walking": Play only notes that are one step away from each other
            on:
            <ul>
              <li>
                "Beat": Every beat a new note
              </li>
              <li>
                "Division": Set a division to play a new note on every division
                or multiplication of a beat
              </li>
            </ul>
          </li>
          <li>
            "Jumpy": Play only notes that are one jump away from each other on:
            <ul>
              <li>
                "Beat": Every beat a new note
              </li>
              <li>
                "Division": Set a division to play a new note on every division
                or multiplication of a beat
              </li>
            </ul>
          </li>
          <li>
            "_other_suggestions_welcome_"
          </li>
        </ul>
      </li>
    </ul>
  </li>
</ul>

<h3>Multi-voice Variables:</h3>
<ul>
  <li>
    Set "Dissonant Resolutions": In WCM, one of the notes in a dissonant interval
    typically resolves downward into an imperfectly consonant interval. "harm"
    users must decide whether a dissonant note should resolve upwards or
    downwards into another interval, or not, and indicate whether that interval
    is or may be consonant or dissonant and to which level. This setting leads
    primarily the generation of the next harmony, other variables/restrictions
    are considered later on in this process.
    <ul>
      <li>
        "Up":
        <ul>
          <li>
            "{_defined-dissonance-or-consonance-level-here_}"
          </li>
        </ul>
      </li>
      <li>
        "Down":
        <ul>
          <li>
            "{_defined-dissonance-or-consonance-level-here_}"
          </li>
        </ul>
      </li>
    </ul>
  </li>
  <li>
    Set the "Interval Parallels Allowance": In WCM, the use of "perfect octave"
    and "perfect fifth" parallels is generally discouraged, and "dissonant"
    parallels are considered problematic. Users can specify which parallels are
    allowed or forbidden.
    <ul>
      <li>
        "Yes":
        <ul>
          <li>
            "Maximum Consonance": Set the maximum conconance level. Standard
            WCM defines "Imperfect Consonant".
          </li>
          <li>
            "Maximum Dissonance": Set the maximum disconance level. Standard
            WCM defines "Mild Dissonant".
          </li>
        </ul>
      </li>
      <li>
        "No"
      </li>
    </ul>
  </li>
  <li>
    Set the "Rate of Simultaneous Movements": The minimum value is "1", allowing
    only one note to transition to a new note, with dissonants taking precedence
    over consonants, based on their dissonance level. The maximum value is "0"
    (no maximum), where all voices can move at the same time.
    <ul>
      <li>
        "_enter_a_number_": Too large numbers fall back to "0".
      </li>
    </ul>
  </li>
</ul>

The program must facilitate the input of a melody along with its time unit
using basic Lilypond syntax. It should generate a harmonic "accompaniment" in
straightforward Lilypond syntax for PDF score and MIDI file output, while also
issuing relevant error and warning messages when certain actions cannot be
performed. Furthermore, it should provide all possible results, and the option
to combine portions of different calculations.

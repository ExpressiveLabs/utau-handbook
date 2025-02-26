- ## Kinds of aliases in VCCV 2015
    - `[-V]`
      - Meant for when a syllable starts with a vowel next to silence
    - `[V]`
      - Meant to extend vowels across notes
    - `[_V]`
      - Meant for when your missing a `[CV]` (mostly, in this case, for `[ngV]`) and to be used with the C_k system (See C_k system for more)
    - `[V-]`
      - Meant for when a syllable ends in a vowel next to silence    
    - `[-CV]`
      -  Meant for `/CV/` pairs that are next to silences
    - `[CV]`
        - Meant for `/CV/` pairs that are next to vowels or consonants from the last syllable
    - `[_CV]`
        - Meant to be combined with onset `[CC]`s to form onset consonant clusters
        - the only consonants are `[r]` `[l]` `[y]` and `[w]`
    - Onset `[-CC]`
        - Meant to be combinde with `[_CV]` (or `[CV]`s if a `[_CV]` isn't available) to form onset consonant clusters that are next to silences
    - Onset `[CC]`
        - Meant to be combinde with `[_CV]` (or `[CV]`s if a `[_CV]` isn't available) to form onset consonant clusters that are next to vowels or consonants from the last syllable
    - Coda `[CC]`
      - Falls under the C_k system
      - Meant to be combinde with `[VC-]`s to form coda consonant clusters next to vowels (see C_k system for more) or consonants from the next syllable
    - Coda `[CC-]`
      -   Meant to be combinde with `[VC-]`s to form coda consonant clusters next to sillence, or to be used as a replacement for Coda `[CC]`s for softer consonants
    - Coda `[VCC]`
      - Falls under the C_k system
      - Coda consonant clusters used next to vowels (see C_k system for more) or consonants from the next syllable
    - Coda `[VCC-]`
      - Coda consonant clusters used next to next to sillence, or to be used as a replacement for Coda `[VCC]`s for softer consonants
    - `[VC]`
        - Falls under the C_k system
        - Meant to be used for singualar coda consonants next to other consonants or next to a vowel when the consonant doesn't fall on the same syllable (see VC_k system for more)
    - `[V C]`
        - Meant to transion from a vowel to a consonent that falls on the next syllable
    - `[VC-]`
        - Meant to transion from a vowel to a consonent that falls on the same syllable, to be put next to silence when a syllable ends in a consonent, or as a replacement for a `[VC]` for a softer consonant.
    - `[C C]`
        - Meant to be combinded with a `[VC-]` to functions like a `[VC]` but a specific consonant transtion instead of a `[k]` or `[t]`.
      
- ## C_k System
  - The C_k system refers to how VCCV 2015 uses C_k aliases and `[CV]`/`[_V]` for `[C.CV]` or `[C.V]` connections.
  - When a syllable ends in a consonant and the next Syllable is just a vowel, using a `C_k[_V]` pair will reasult in the consonant sounding like it's comeing from the last syllable instead of the next one like how using a `[V C][CV]` pair may make things sound. (See Consonant Syllable Placement for more)

- ## Consonant Syllable Placement
  - VCCV as a system cares deeply about where Consonants fall in syllables, it changes what type of allies is used depending on where they fall.
    - Examples
      - `[p@s.p0rt]` should be parsed as `[-p@][@s][p0][0r-][rt-]` while `[p@.sp0rt]` should be `[-p@][@ sp][sp0][0r-][rt-]`.
      - `[ku.myu.ni.ddE]` should be `[-ku][u m][my][_yo][o n][ni][i dd][ddE]` while `[kum.yu.ni.ddE]` should be `[-ku][um-][m y][yo][o n][ni][i dd][ddE]`.
      - `[vAr.E]` should be `[-vA][Ar-][rE]` while `[vA.rE]` should be `[-vA][A r][rE]`.
  - In order for this to be intuetive for the user, it should be clear where consonants fall in syllables
      - Examples
          - SynthV

            ![image](https://github.com/user-attachments/assets/8b0cc2f7-5954-413d-a70b-bc1b98109f80)
            - Makes it very clear that the `[s]` and `[p]` fall on two different syllables
        - OpenUTAU
       
          ![image](https://github.com/user-attachments/assets/c8a72639-9ce2-470b-9682-2a819e5e9646)
            - It's very vague where the `[s]` and `[p]` fall, which makes it unclear how this is being parsed
    - Where consonants should fall is determined by stress, more research is needed to understand how stress and consonant syllable placement interact.

    -  ##  Timings
      -  One of the core principles of VCCV is that it handles the timings of Phonemes for you.
      -  The timing for everything is based on the next notes Pre-utterance, except for `[CV]`s and `[-CV]`s.
      -  VCCV relies on Consonant Velocity in order to make sure things sound natural when songs are sung quickly or when there's a lot of fast notes
          - The nice thing about this is that it's extremely consistent, being able to be handled with some math.
          -  There are three different math equations to know about with VCCV, one for BPM, notes faster then 480 and notes slower then 480
              - The one for BPM is $$100 \left(\frac{\text{Song's BPM}}{120}\right) = \text{Default velocity}$$.
                    This equation adjusts the length of the note's pre-utterance to be as if it was recorded at the BPM of the song
              - The one for notes faster then 480 is<br>
                `(100 - (100 * (note_length / 480))) + default_velocity`
              - The one for notes slower then 480 is<br>
                `default_velocity - (-50 + (100 * (note_length / 960)))`




  

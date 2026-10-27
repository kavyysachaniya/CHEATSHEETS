# LJU Engineering Aptitude — LaTeX Cheatsheets

> Formulae use standard LaTeX display math (`$$ ... $$`). Preview in a Markdown editor that supports LaTeX math, such as Obsidian, Typora, or VS Code with a compatible Markdown math extension.

## Contents

- [Calendar](#calendar)
- [Direction Sense](#direction-sense)
- [Blood Relations](#blood-relations)
- [Coding and Decoding](#coding-and-decoding)
- [Miscellaneous Reasoning](#miscellaneous-reasoning)
- [Percentage](#percentage)
- [Profit and Loss](#profit-and-loss)
- [Partnership](#partnership)
- [Simple Interest](#simple-interest)
- [Time, Speed and Distance](#time-speed-and-distance)
- [Problems on Trains](#problems-on-trains)
- [Boats and Streams](#boats-and-streams)
- [Time and Work](#time-and-work)
- [Pipes and Cisterns](#pipes-and-cisterns)
- [Chain Rule — Work in Groups](#chain-rule-work-in-groups)
- [Number System](#number-system)
- [LCM and HCF](#lcm-and-hcf)
- [Average](#average)
- [Ratio and Proportion](#ratio-and-proportion)
- [Alligation and Mixture](#alligation-and-mixture)
- [Races and Games](#races-and-games)

---

## Calendar

**Syllabus block:** Unit 02 · Logical Reasoning – Puzzle Solving · **Weightage:** 19% · **Reference scope:** Syllabus Unit 02; R.S. Aggarwal, Calendar chapter (pp. 819–822)

### Cheatsheet

#### CORE RULES

- Ordinary year = 365 days = 1 odd day.
- Leap year = 366 days = 2 odd days.
- Odd days are the remainder after dividing total days by 7.

#### LEAP YEARS

- A year divisible by 4 is usually leap.
- A century year must be divisible by 400 (so 2000 is leap, 2100 is not).

#### DAY SHIFT

- Move forward by N days: add N mod 7 to the weekday.
- Move backward by N days: subtract N mod 7.
- For dates within one year, count the days between dates, then take mod 7.

#### QUICK CHECKS

- Same date next ordinary year shifts by 1 weekday; after a leap year by 2, provided the interval includes that leap year.
- 7, 14, 21… days do not change the weekday.

#### CAUTION

- For a date-to-date calculation, exclude the starting date and count the elapsed days.
- Gregorian century exceptions break the simple 28-year repetition rule.

### Key formulas (LaTeX)

#### Ordinary year: odd days

$$
365 = 52\times 7 + 1 \quad\Rightarrow\quad 365\bmod 7=1
$$

An ordinary year leaves 1 odd day.

#### Leap year: odd days

$$
366 = 52\times 7 + 2 \quad\Rightarrow\quad 366\bmod 7=2
$$

A leap year leaves 2 odd days.

#### Weekday shift

$$
\text{New weekday index}\equiv (\text{Starting index}+d)\pmod 7
$$

Use elapsed days d; the remainder tells how far the weekday advances.

#### Gregorian leap-year rule

$$
(y\bmod 400=0)\;\lor\;\big[(y\bmod 4=0)\land(y\bmod 100\ne 0)\big]
$$

A century year must be divisible by 400 to be a leap year.

---

## Direction Sense

**Syllabus block:** Unit 02 · Logical Reasoning – Puzzle Solving · **Weightage:** 19% · **Reference scope:** Syllabus Unit 02; direction-sense topic listed in syllabus

### Cheatsheet

#### COMPASS

- North is up, East right, South down, West left.
- Right/left turns are relative to the direction you are currently facing.

#### TURN TRICK

- Facing N: right E, left W.
- Facing E: right S, left N.
- Facing S: right W, left E.
- Facing W: right N, left S.

#### NET DISPLACEMENT

- Cancel opposite movements (N against S, E against W).
- The remaining horizontal and vertical components give the final direction.

#### SHORTEST DISTANCE

- For perpendicular components a and b, shortest distance = √(a²+b²).
- Remember common triples: 3–4–5, 5–12–13, 8–15–17, 7–24–25.

#### EXAM TIP

- Track the final facing direction separately from the final position; they are not necessarily the same thing.

### Key formulas (LaTeX)

#### Shortest distance from perpendicular movements

$$
d=\sqrt{(\Delta x)^2+(\Delta y)^2}
$$

Use the net east–west and north–south movements as the two perpendicular components.

#### Net horizontal movement

$$
\Delta x=|E-W|
$$

Subtract westward distance from eastward distance; the larger direction determines whether the net is east or west.

#### Net vertical movement

$$
\Delta y=|N-S|
$$

Subtract southward distance from northward distance; the larger direction determines whether the net is north or south.

#### Common Pythagorean triples

$$
3^2+4^2=5^2,\quad 5^2+12^2=13^2,\quad 8^2+15^2=17^2
$$

Memorise these to calculate common shortest-distance questions mentally.

---

## Blood Relations

**Syllabus block:** Unit 02 · Logical Reasoning – Puzzle Solving · **Weightage:** 19% · **Reference scope:** Syllabus Unit 02; blood-relations topic listed in syllabus

### Cheatsheet

#### DRAW A FAMILY TREE

- Place each generation on a separate row.
- Mark gender only when the question states it; do not infer gender from names.

#### GENERATION CLUES

- Father/mother = one generation above; son/daughter = one below; grandfather/grandmother = two above; grandson/granddaughter = two below.

#### SIBLINGS & IN-LAWS

- Brother/sister share a parent.
- Uncle/aunt is a parent’s sibling.
- A spouse’s parent is a parent-in-law; a spouse’s sibling is a brother/sister-in-law.

#### SOLVING ORDER

- Translate one statement at a time and follow the chain from the person asked about.
- Watch the viewpoint: “How is X related to Y?” asks X’s relation to Y.

#### TRICK

- Write A → B as “A is … of B” to avoid reversing the relationship.

### Key formulas (LaTeX)

#### Generation tracking convention

$$
g(\text{parent})=+1,\quad g(\text{child})=-1
$$

One consistent convention is to count upward generations as +1 and downward generations as −1. The family-tree relationship still determines the final answer.

#### Relationship-chain notation

$$
A\xrightarrow{\text{is the parent of}}B
$$

Write each statement from the first person’s point of view; do not reverse “X is related to Y”.

---

## Coding and Decoding

**Syllabus block:** Unit 01 · Logical Reasoning – Series and Analogy · **Weightage:** 14% · **Reference scope:** Syllabus Unit 01; coding and decoding listed in syllabus

### Cheatsheet

#### LETTER POSITIONS

- A=1, B=2, …, Z=26.
- Check whether letters are shifted forward/backward by a fixed number.

#### COMMON PATTERNS

- Look for reverse order, opposite letters (A↔Z, B↔Y), alternating shifts, increasing shifts, letter-position sums, and vowel/consonant rules.

#### WRAPAROUND

- After Z, continue from A; before A, continue from Z.
- Write the alphabet positions when a pattern is unclear.

#### VERIFY THE RULE

- Infer a rule from the example, then apply exactly the same rule to every letter.
- Do not pick a pattern that matches only the first or last letter.

#### QUICK TEST

- Check shift differences first; if not constant, test reverse order and alternating/increasing shifts next.

### Key formulas (LaTeX)

#### Alphabet positions

$$
\operatorname{pos}(A)=1,\;\operatorname{pos}(B)=2,\;\ldots,\;\operatorname{pos}(Z)=26
$$

Convert letters to positions before comparing shifts.

#### Forward/backward letter shift

$$
p\prime=\big((p-1+k)\bmod 26\big)+1
$$

p is the original position and k is the signed shift. The formula wraps Z back to A.

#### Opposite letters

$$
p\prime=27-p
$$

A ↔ Z, B ↔ Y, C ↔ X, and so on.

---

## Miscellaneous Reasoning

**Syllabus block:** Unit 01 · Logical Reasoning – Series and Analogy · **Weightage:** 14% · **Reference scope:** Syllabus Unit 01: series, analogy, classification, arithmetical reasoning, mathematical operation and data sufficiency

### Cheatsheet

#### NUMBER SERIES

- Check first differences, second differences, multiplication/division, alternating sequences, squares/cubes, and prime numbers.

#### LETTER SERIES

- Convert letters to positions (A=1…Z=26); compare jumps and check wraparound.

#### ANALOGY

- Identify the exact relationship in the pair (function, part-to-whole, category, degree, cause/effect) and apply it to the second pair.

#### CLASSIFICATION

- Find the one item that does not follow the shared property; test category, parity, divisibility, spelling or sequence.

#### DATA SUFFICIENCY

- Test each statement independently first.
- Decide whether it uniquely answers the question; do not solve more than is needed.

#### MATH OPERATIONS

- Replace symbols exactly as defined, then use BODMAS.
- Keep brackets intact and check whether the transformed statement is true.

### Key formulas (LaTeX)

#### First difference of a sequence

$$
\Delta a_n=a_{n+1}-a_n
$$

Check first differences when a number sequence is not obviously arithmetic or geometric.

#### Second difference

$$
\Delta^2 a_n=\Delta a_{n+1}-\Delta a_n
$$

Constant second differences often indicate a quadratic pattern.

#### Letter-position mapping

$$
A=1,\;B=2,\;\ldots,\;Z=26
$$

For letter series, compare numerical jumps and check whether the alphabet wraps around.

---

## Percentage

**Syllabus block:** Unit 07 · Quantitative Aptitude – Clerical Aptitude · **Weightage:** 13% · **Reference scope:** R.S. Aggarwal, Percentage (pp. 308–373); syllabus Unit 07

### Cheatsheet

#### CORE FORMULA

- x% of N = (x/100) × N.
- Percentage = (part/whole) × 100.

#### CHANGE

- New value = old value × (1 ± p/100).
- Two successive changes p% and q% combine to p + q + pq/100, with decreases entered as negative values.

#### REVERSE PERCENT

- If a value after a p% increase is known, original = final ÷ (1 + p/100).
- For a discount, divide by (1 − p/100).

#### MENTAL SHORTCUTS

- 10%=one tenth; 5%=half of 10%; 25%=one quarter; 12.5%=one eighth; 33⅓%=one third; 50%=half.

#### CAUTION

- A 20% increase followed by a 20% decrease is not zero change: multiply 1.2 × 0.8 = 0.96, a 4% decrease.

### Key formulas (LaTeX)

#### Percentage of a quantity

$$
x\%\text{ of }N=\frac{x}{100}\times N
$$

To find x% of N, multiply N by x/100.

#### Convert part to percentage

$$
\text{Percentage}=\frac{\text{Part}}{\text{Whole}}\times100\%
$$

The whole is the reference total.

#### Increase or decrease by p%

$$
\text{New value}=\text{Old value}\left(1\pm\frac{p}{100}\right)
$$

Use + for an increase and − for a decrease.

#### Two successive percentage changes

$$
\text{Net change (\%)}=p+q+\frac{pq}{100}
$$

Enter a decrease as a negative percentage. For +20% then −20%, the net change is −4%.

---

## Profit and Loss

**Syllabus block:** Unit 07 · Quantitative Aptitude – Clerical Aptitude · **Weightage:** 13% · **Reference scope:** R.S. Aggarwal, Profit and Loss (pp. 374–425); syllabus Unit 07

### Cheatsheet

#### BASE AMOUNT

- Profit = SP − CP; Loss = CP − SP.
- Profit% and loss% are normally calculated on cost price (CP).

#### SELLING PRICE

- At p% profit: SP = CP × (100+p)/100.
- At p% loss: SP = CP × (100−p)/100.

#### DISCOUNT

- Discount = Marked Price − Selling Price.
- Discount% = discount/marked price × 100.
- A markup and discount apply successively.

#### SUCCESSIVE DEALS

- For successive profit rates, multiply selling-price factors; do not simply add percentages unless the bases match.

#### SHORTCUTS

- Same selling price with x% gain on one item and x% loss on the other gives a net loss of x²/100%.

### Key formulas (LaTeX)

#### Profit and loss

$$
\text{Profit}=\text{SP}-\text{CP},\qquad \text{Loss}=\text{CP}-\text{SP}
$$

SP means selling price; CP means cost price.

#### Profit percentage / loss percentage

$$
\text{Profit\%}=\frac{\text{Profit}}{\text{CP}}\times100\%,\qquad \text{Loss\%}=\frac{\text{Loss}}{\text{CP}}\times100\%
$$

Unless stated otherwise, profit and loss percentages are calculated on cost price.

#### Selling price at p% profit or loss

$$
\text{SP}=\text{CP}\left(1+\frac{p}{100}\right)\quad\text{(profit)}
$$

For a loss, use SP = CP(1 − p/100).

#### Discount percentage

$$
\text{Discount\%}=\frac{\text{Marked Price}-\text{SP}}{\text{Marked Price}}\times100\%
$$

Discount percentage uses marked price as its base.

---

## Partnership

**Syllabus block:** Unit 07 · Quantitative Aptitude – Clerical Aptitude · **Weightage:** 13% · **Reference scope:** R.S. Aggarwal, Partnership (pp. 476–492); syllabus Unit 07

### Cheatsheet

#### SHARE RATIO

- When partners invest for different periods, profit share is proportional to capital × time.

#### CAPITAL CHANGES

- Split a partner’s investment into time intervals whenever money is added or withdrawn; add each capital×months contribution.

#### DIVIDE PROFIT

- If contributions are in ratio a:b:c and total profit is P, first add the ratio parts, then each share = P × its part / total parts.

#### WORKING TIP

- Use the same time unit for all partners (usually months).
- Investment amount alone is not enough when time differs.

#### CHECK

- Shares should add back to the total profit; simplify the contribution ratio before dividing.

### Key formulas (LaTeX)

#### Profit-sharing contribution

$$
\text{Contribution}_i=\text{Capital}_i\times\text{Time}_i
$$

Convert investment periods to the same unit, usually months.

#### A partner’s share of profit

$$
\text{Share}_i=P\times\frac{C_i t_i}{\sum_j C_jt_j}
$$

P is total profit, C is invested capital, and t is the investment duration.

#### Two partners’ ratio

$$
A:B=C_A t_A:C_B t_B
$$

When investment periods are equal, profit is shared in the capital ratio.

---

## Simple Interest

**Syllabus block:** Unit 07 · Quantitative Aptitude – Clerical Aptitude · **Weightage:** 13% · **Reference scope:** R.S. Aggarwal, Simple Interest (pp. 641–662); syllabus Unit 07

### Cheatsheet

#### MAIN FORMULA

- Simple Interest (SI) = (Principal × Rate × Time)/100.
- Amount = Principal + SI.

#### UNITS

- Rate is normally per annum.
- Convert months to years (months/12) and days to the stated year convention before substitution.

#### REARRANGE

- Principal = SI×100/(Rate×Time); Rate = SI×100/(Principal×Time); Time = SI×100/(Principal×Rate).

#### RATIO TRICK

- At the same principal and time, SI is proportional to rate.
- At the same rate, SI is proportional to principal and time.

#### DISTINGUISH

- Simple interest is calculated on the original principal every period, unlike compound interest where interest earns interest.

### Key formulas (LaTeX)

#### Simple interest

$$
\mathrm{SI}=\frac{P\times R\times T}{100}
$$

P = principal, R = annual rate in percent, and T = time in years.

#### Total amount

$$
A=P+\mathrm{SI}
$$

Amount is principal plus the simple interest earned.

#### Rearranged formulas

$$
P=\frac{100\,\mathrm{SI}}{RT},\qquad R=\frac{100\,\mathrm{SI}}{PT},\qquad T=\frac{100\,\mathrm{SI}}{PR}
$$

Use these when principal, rate, or time is unknown; keep rate and time units consistent.

---

## Time, Speed and Distance

**Syllabus block:** Unit 09 · Quantitative Aptitude – Physical Aptitude · **Weightage:** 13% · **Reference scope:** R.S. Aggarwal, Time and Distance (pp. 562–599); syllabus Unit 09

### Cheatsheet

#### BASIC FORMULAS

- Distance = Speed × Time; Speed = Distance/Time; Time = Distance/Speed.

#### UNIT CONVERSION

- km/h → m/s: multiply by 5/18. m/s → km/h: multiply by 18/5.

#### AVERAGE SPEED

- Average speed = total distance / total time.
- For equal distances at speeds a and b, average speed = 2ab/(a+b), not (a+b)/2.

#### RELATIVE SPEED

- Toward each other: add speeds.
- Same direction: subtract the slower speed from the faster speed.

#### RATIO TRICK

- For the same distance, time is inversely proportional to speed.
- For the same time, distance is proportional to speed.

### Key formulas (LaTeX)

#### Distance, speed, and time

$$
v=\frac{d}{t},\qquad d=vt,\qquad t=\frac{d}{v}
$$

Use consistent units for distance and time.

#### Speed conversion

$$
\text{km/h}\times\frac{5}{18}=\text{m/s},\qquad \text{m/s}\times\frac{18}{5}=\text{km/h}
$$

Memorise 5/18 to convert km/h into m/s.

#### Average speed

$$
\text{Average speed}=\frac{\text{Total distance}}{\text{Total time}}
$$

Do not average speeds directly unless the conditions justify it.

#### Equal distances at speeds u and v

$$
v_{\mathrm{avg}}=\frac{2uv}{u+v}
$$

This harmonic-mean shortcut applies only when the two distances are equal.

#### Relative speed

$$
v_{\mathrm{rel}}=u+v\;\text{(opposite directions)},\qquad v_{\mathrm{rel}}=|u-v|\;\text{(same direction)}
$$

For same-direction motion, subtract the slower speed from the faster speed.

---

## Problems on Trains

**Syllabus block:** Unit 09 · Quantitative Aptitude – Physical Aptitude · **Weightage:** 13% · **Reference scope:** R.S. Aggarwal, Problems on Trains (pp. 612–632); syllabus Unit 09

### Cheatsheet

#### CONVERSION

- Convert train speed to m/s (×5/18) when lengths are in metres and time in seconds.

#### CROSSING A POLE

- Time = train length / speed.
- A person or pole is treated as having negligible length.

#### CROSSING A PLATFORM

- Time = (train length + platform length) / speed.

#### TWO TRAINS

- Opposite directions: relative speed is the sum.
- Same direction: relative speed is the difference.
- Crossing distance is the sum of both train lengths.

#### CHECK UNITS

- Length in metres ÷ speed in m/s gives seconds.
- Do not combine km/h directly with metres.

### Key formulas (LaTeX)

#### Train crossing a pole

$$
t=\frac{L}{v}
$$

L is train length; the pole’s length is negligible.

#### Train crossing a platform

$$
t=\frac{L_{\mathrm{train}}+L_{\mathrm{platform}}}{v}
$$

The train must cover its own length plus the platform length.

#### Two trains crossing

$$
t=\frac{L_1+L_2}{v_{\mathrm{rel}}}
$$

Use the sum of train lengths. Relative speed is the sum for opposite directions or the difference for the same direction.

#### Convert before calculating

$$
v\;(\mathrm{m/s})=v\;(\mathrm{km/h})\times\frac{5}{18}
$$

Metres divided by metres per second gives time in seconds.

---

## Boats and Streams

**Syllabus block:** Unit 09 · Quantitative Aptitude – Physical Aptitude · **Weightage:** 13% · **Reference scope:** R.S. Aggarwal, Boats and Streams (pp. 600–611); syllabus Unit 09

### Cheatsheet

#### SPEED RELATIONS

- Downstream speed D = still-water speed u + stream speed v.
- Upstream speed U = u − v.

#### REVERSE FORMULAS

- Still-water speed u = (D+U)/2.
- Stream speed v = (D−U)/2.

#### TIME

- Time = distance/speed; use downstream speed for travel with the current and upstream speed against it.

#### SANITY CHECK

- Downstream must be faster than still-water speed; upstream must be slower.
- If U is negative, check the data.

#### MENTAL TIP

- Adding downstream and upstream speeds cancels the stream; subtracting them doubles the stream speed.

### Key formulas (LaTeX)

#### Downstream and upstream speeds

$$
D=u+v,\qquad U=u-v
$$

D is downstream speed, U is upstream speed, u is still-water speed, and v is stream speed.

#### Recover still-water and stream speeds

$$
u=\frac{D+U}{2},\qquad v=\frac{D-U}{2}
$$

Add the two observed speeds to cancel the current; subtract them to isolate twice the stream speed.

#### Travel time

$$
t=\frac{d}{v}
$$

Use D for downstream journeys and U for upstream journeys.

---

## Time and Work

**Syllabus block:** Unit 09 · Quantitative Aptitude – Physical Aptitude · **Weightage:** 13% · **Reference scope:** R.S. Aggarwal, Time and Work (pp. 526–561); syllabus Unit 09

### Cheatsheet

#### WORK RATE

- If A completes a job in x days, A’s one-day work is 1/x.
- Add rates for people working together.

#### COMBINED TIME

- For A in x days and B in y days, together time = xy/(x+y), assuming they work at constant rates.

#### WORKERS & DAYS

- For equally efficient workers doing the same job, workers × days is constant.
- More workers means fewer days.

#### PARTIAL WORK

- Work done = rate × time.
- Subtract completed work from 1 to find the remaining fraction.

#### CAUTION

- Do not add completion times; add work rates.
- Check that the combined rate is greater than either individual rate.

### Key formulas (LaTeX)

#### One-day work rate

$$
\text{Rate of A}=\frac{1}{x}
$$

If A finishes the whole job in x days, A completes 1/x of the job per day.

#### Two workers together

$$
\frac{1}{T}=\frac{1}{x}+\frac{1}{y}\quad\Rightarrow\quad T=\frac{xy}{x+y}
$$

Add work rates, not the completion times.

#### Work done

$$
\text{Work done}=\text{Rate}\times\text{Time}
$$

Subtract completed work from 1 to find the remaining fraction of a single job.

#### Equal-efficiency workers

$$
\text{Workers}\times\text{Days}=\text{constant}
$$

For the same job and identical daily hours, increasing workers reduces the required days.

---

## Pipes and Cisterns

**Syllabus block:** Unit 09 · Quantitative Aptitude – Physical Aptitude · **Weightage:** 13% · **Reference scope:** R.S. Aggarwal, Pipes and Cisterns (pp. 510–525); syllabus Unit 09

### Cheatsheet

#### FILLING & EMPTYING

- A pipe filling a tank in x hours has rate +1/x tank per hour.
- An outlet emptying it in y hours has rate −1/y.

#### NET RATE

- Add all open-pipe rates with signs.
- Time to fill = 1/(net filling rate), if the net rate is positive.

#### PARTIAL OPENING

- Work done in t hours = net rate × t.
- If pipes change state, calculate each time interval separately.

#### VOLUME

- If flow rate is given in litres/minute, volume = rate × time in minutes.

#### CHECK

- A leak should increase the time needed.
- If calculated net rate is zero or negative, the tank will not fill while those pipes remain open.

### Key formulas (LaTeX)

#### Net filling rate

$$
R_{\mathrm{net}}=\sum_i\frac{1}{x_i}-\sum_j\frac{1}{y_j}
$$

Each inlet has positive rate 1/x; each outlet/leak has negative rate 1/y.

#### Time to fill or empty

$$
T=\frac{1}{|R_{\mathrm{net}}|}
$$

Use the appropriate direction. The tank fills only when the net rate is positive.

#### Volume from flow rate

$$
V=q\times t
$$

If q is in litres per minute, use time in minutes to obtain litres.

---

## Chain Rule — Work in Groups

**Syllabus block:** Unit 09 · Quantitative Aptitude – Physical Aptitude · **Weightage:** 13% · **Reference scope:** R.S. Aggarwal, Chain Rule (pp. 493–509); syllabus Unit 09

### Cheatsheet

#### FIXED WORK

- For equally efficient workers, workers × days = constant.
- If daily hours vary, workers × hours/day × days = constant.

#### EFFICIENCY

- If efficiencies differ, multiply by efficiency as well.
- Work ∝ workers × time × hours × efficiency.

#### DIRECT/INVERSE

- More workers, hours or efficiency means fewer days for a fixed job.
- More work means more days.

#### THREE-FACTOR METHOD

- Set the old and new work expressions equal, then solve for the unknown.
- Keep units consistent.

#### PARTLY COMPLETED JOB

- Calculate work completed by the first group, subtract from total work, then divide remaining work by the new group’s daily capacity.

### Key formulas (LaTeX)

#### Equal job with equal efficiency

$$
W\propto n\times h\times d
$$

For the same job, workers n, daily hours h, and days d are inversely related when other factors are fixed.

#### Include efficiency

$$
W\propto n\times h\times d\times e
$$

Include e when worker efficiency differs. Keep hours/day and days consistent.

#### Compare two arrangements

$$
n_1h_1d_1e_1=n_2h_2d_2e_2
$$

For equal amounts of work, set the two work expressions equal and solve for the unknown.

---

## Number System

**Syllabus block:** Unit 03 · Numerical Ability – Number System · **Weightage:** 11% · **Reference scope:** R.S. Aggarwal, Number System (pp. 3–50); syllabus Unit 03

### Cheatsheet

#### NUMBER TYPES

- Natural numbers: 1,2,3…; whole numbers include 0; integers include negatives.
- 1 is neither prime nor composite; 2 is the only even prime.

#### DIVISIBILITY

- 2: even last digit; 3 or 9: digit sum divisible by 3 or 9; 4: last two digits divisible by 4; 5: last digit 0/5; 8: last three digits divisible by 8; 11: alternating digit-sum difference is 0 or a multiple of 11.

#### FACTORIZATION

- If n = p^a q^b, number of positive factors = (a+1)(b+1)… .
- Use prime factorization to test perfect squares/cubes.

#### REMAINDERS & LAST DIGITS

- Use modular arithmetic.
- Last digits of powers repeat in cycles; reduce the exponent by the cycle length.

#### MENTAL CHECKS

- For largest/smallest multiples, divide and take floor/ceiling.
- For trailing zeros in n!, add ⌊n/5⌋ + ⌊n/25⌋ + ⌊n/125⌋ + … .

### Key formulas (LaTeX)

#### Number of positive divisors

$$
n=p_1^{a_1}p_2^{a_2}\cdots p_k^{a_k}\quad\Rightarrow\quad d(n)=\prod_{i=1}^{k}(a_i+1)
$$

Write n as a prime factorisation; add 1 to every exponent and multiply.

#### Trailing zeroes in n!

$$
Z(n!)=\left\lfloor\frac{n}{5}\right\rfloor+\left\lfloor\frac{n}{25}\right\rfloor+\left\lfloor\frac{n}{125}\right\rfloor+\cdots
$$

Continue powers of 5 until the divisor exceeds n.

#### Remainder notation

$$
a\equiv r\pmod m
$$

This means a leaves remainder r when divided by m.

---

## LCM and HCF

**Syllabus block:** Unit 03 · Numerical Ability – Number System · **Weightage:** 11% · **Reference scope:** R.S. Aggarwal, H.C.F. and L.C.M. of Numbers (pp. 51–68); syllabus Unit 03

### Cheatsheet

#### HCF

- Highest common factor is the greatest number dividing every number.
- Prime factorization uses the smallest exponent of each common prime.

#### LCM

- Least common multiple is the smallest positive number divisible by all given numbers.
- Prime factorization uses the greatest exponent of each prime.

#### TWO-NUMBER IDENTITY

- For positive integers a and b: HCF(a,b) × LCM(a,b) = a × b.

#### APPLICATIONS

- Use HCF for largest equal pieces or largest measure; use LCM for repeated events that need to coincide.

#### REMAINDERS

- If a number leaves the same remainder r on division by several divisors, subtract r first; then use HCF/LCM as appropriate.

### Key formulas (LaTeX)

#### HCF–LCM identity for two positive integers

$$
\operatorname{HCF}(a,b)\times\operatorname{LCM}(a,b)=a\times b
$$

This product identity applies to a pair of positive integers.

#### Prime-factor method

$$
\mathrm{HCF}:\text{ smallest common exponents},\qquad \mathrm{LCM}:\text{ greatest exponents}
$$

For HCF take the smallest exponent of each common prime; for LCM take the largest exponent of every prime present.

---

## Average

**Syllabus block:** Unit 03 · Numerical Ability – Number System · **Weightage:** 11% · **Reference scope:** R.S. Aggarwal, Average (pp. 206–239); syllabus Unit 03

### Cheatsheet

#### MAIN FORMULA

- Average = sum of observations / number of observations.
- Therefore, total = average × count.

#### ADD/REMOVE

- When one observation is added or removed, update the total first, then divide by the new count.

#### REPLACEMENT

- If x is replaced by y, the total changes by y−x; average changes by (y−x)/n.

#### COMBINED AVERAGE

- Combined average = (n₁a₁+n₂a₂)/(n₁+n₂), a weighted mean rather than a simple average of averages.

#### QUICK TRICKS

- The average of consecutive equally spaced numbers is the middle value; for an odd count it is the central term.

### Key formulas (LaTeX)

#### Average and total

$$
\bar{x}=\frac{\sum_{i=1}^{n}x_i}{n},\qquad \text{Total}=\bar{x}\times n
$$

The sum of all observations is the average multiplied by the count.

#### Average after replacing x by y

$$
\text{New average}=\text{Old average}+\frac{y-x}{n}
$$

The count n stays unchanged when one value is replaced.

#### Combined average of two groups

$$
\bar{x}=\frac{n_1\bar{x}_1+n_2\bar{x}_2}{n_1+n_2}
$$

Use group sizes as weights; do not simply average the two averages unless group sizes are equal.

---

## Ratio and Proportion

**Syllabus block:** Unit 08 · Quantitative Aptitude – Arithmetic Aptitude · **Weightage:** 4% · **Reference scope:** R.S. Aggarwal, Ratio and Proportion (pp. 426–475); syllabus Unit 08

### Cheatsheet

#### RATIO

- a:b = a/b.
- Multiply or divide both terms by the same non-zero number without changing the ratio.

#### DIVIDING A TOTAL

- If a total T is divided in ratio m:n, shares are T×m/(m+n) and T×n/(m+n).

#### COMPOUND RATIO

- If A:B = m:n and B:C = p:q, make the B terms equal, then combine the ratios.

#### PROPORTION

- a:b = c:d means ad = bc.
- Fourth proportional d = bc/a.

#### DIRECT/INVERSE

- For direct proportion, the ratio stays constant; for inverse proportion, product stays constant.

### Key formulas (LaTeX)

#### Ratio and proportion

$$
a:b=\frac{a}{b},\qquad \frac{a}{b}=\frac{c}{d}\Rightarrow ad=bc
$$

Cross-multiplication works when the denominators are non-zero.

#### Divide total T in ratio m:n

$$
\text{First share}=T\frac{m}{m+n},\qquad \text{Second share}=T\frac{n}{m+n}
$$

Add the ratio parts first, then allocate the total proportionally.

#### Fourth proportional

$$
 d=\frac{bc}{a}\quad\text{when }a:b=c:d
$$

This follows directly from ad = bc.

---

## Alligation and Mixture

**Syllabus block:** Unit 08 · Quantitative Aptitude – Arithmetic Aptitude · **Weightage:** 4% · **Reference scope:** R.S. Aggarwal, Alligation or Mixture (pp. 633–640); syllabus Unit 08

### Cheatsheet

#### WEIGHTED MEAN

- Mixture price/concentration = (quantity₁×value₁ + quantity₂×value₂)/(total quantity).

#### ALLIGATION

- For cheaper value C, dearer value D and mean M: cheaper:dearer quantities = (D−M):(M−C).
- The mean must lie between C and D.

#### CONCENTRATIONS

- Treat pure ingredient as 100% and water as 0%.
- Track the amount of active ingredient separately from total volume.

#### REPLACEMENT

- When x litres are removed from a well-mixed vessel, each ingredient is removed in the existing proportion; then add the replacement liquid.

#### QUICK METHOD

- For water added to a solution, solute amount stays fixed.
- Use solute = concentration × volume before and after.

### Key formulas (LaTeX)

#### Weighted mean of two ingredients

$$
M=\frac{q_1v_1+q_2v_2}{q_1+q_2}
$$

q denotes quantity and v denotes price or concentration value.

#### Alligation ratio

$$
\text{Cheaper:Dearer}=(D-M):(M-C)
$$

C is the cheaper value, D is the dearer value, and M is the target mean. M must lie between C and D.

#### Amount of active ingredient

$$
\text{Solute amount}=\text{Concentration fraction}\times\text{Total volume}
$$

Keep the amount of solute separate from the total solution volume when water is added or evaporates.

---

## Races and Games

**Syllabus block:** Unit 10 · Quantitative Aptitude – Problem Solving Methods · **Weightage:** 4% · **Reference scope:** R.S. Aggarwal, Races and Games of Skill (pp. 814–818); syllabus Unit 10

### Cheatsheet

#### SPEED RATIO

- For equal distances, speed ratio is the inverse of time ratio.
- If A finishes 100 m in 10 s and B in 12 s, speed ratio A:B = 6:5.

#### HEAD START

- If A gives B a head start of h in a race length L and they finish together, distance ratio is L:(L−h), which is also their speed ratio if time is equal.

#### BEATING BY DISTANCE

- If A finishes L while B covers L−d in the same time, speed ratio A:B = L:(L−d).

#### RACE GAP

- At the time A finishes, find B’s distance using B’s speed × A’s time.
- The difference from the finish line is the winning margin.

#### GAMES OF POINTS

- If A can give B p points in a game of n points, their strength/speed ratio is n:(n−p), assuming equal finish time.

### Key formulas (LaTeX)

#### Speed ratio for equal time

$$
v_A:v_B=d_A:d_B
$$

In the same time, speeds are in the same ratio as distances travelled.

#### Speed ratio for equal distances

$$
v_A:v_B=t_B:t_A
$$

For equal distances, speed is inversely proportional to time.

#### A beats B by d in race length L

$$
v_A:v_B=L:(L-d)
$$

When A finishes, B has travelled L−d; both distances were covered in the same time.

#### Head start / points game

$$
v_A:v_B=L:(L-h)\quad\text{or}\quad n:(n-p)
$$

For a head start h in a race of length L, or p points in an n-point game, assume they finish in the same time.

---

*Prepared for LJU Engineering Aptitude revision. Original cheatsheet text is retained, with key formulae added in standard LaTeX notation.*

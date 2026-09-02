# MVP CORE IMPLEMENTATION PLAN
## SaaS EdTech Platform — Product, Business, Technical & Delivery Plan

> **Document Type:** MVP Core Implementation Plan  
> **Purpose:** Product/Engineering Meeting & Execution Reference  
> **Status:** Working Baseline — Final decisions must be recorded in the Decision Log  
> **Target:** Production-ready MVP designed to scale to hundreds of thousands of students  
> **Architecture Direction:** Modular Monolith + Clean Architecture, with clear boundaries for future extraction  
> **Primary Model:** B2C  
> **Core Pillars:** Learning + Internship + Mentoring

---

# 1. HOW TO USE THIS DOCUMENT

هذا الملف ليس مجرد Feature List.

هو الـsingle working document الذي يربط:

- Product decisions
- Business rules
- User journeys
- Domain model
- Backend implementation
- Frontend implementation
- AI
- QA
- Data
- DevOps
- Security
- Scalability
- Sprint execution
- Open questions
- Acceptance Criteria

كل Section يحتوي على:

1. **What we are building**
2. **Business rules**
3. **Implementation**
4. **Acceptance Criteria**
5. **Meeting Questions**
6. **Open Decisions**

أي حاجة غير محسومة لا يتم افتراضها داخل الـimplementation؛ يتم تسجيلها كـ`[OPEN]`.

---

# 2. STATUS LEGEND

| Status | Meaning |
|---|---|
| `[DECIDED]` | تم الاتفاق عليها |
| `[OPEN]` | محتاجة قرار |
| `[RECOMMENDED]` | Recommendation قابلة للتعديل |
| `[PHASE 2]` | خارج Core MVP |
| `[BLOCKER]` | لا يمكن إكمال الجزء بدون القرار |

---

# 3. PRODUCT VISION

## 3.1 Product Concept

المنصة عبارة عن SaaS EdTech Platform هدفها تحويل الطالب أو الـfresh graduate من مرحلة:

> Learning → Practice → Internship → Mentoring → Evaluation → Career Readiness

بدل ما تكون مجرد Course Marketplace.

الـCore Differentiator هو **Internship Simulation**:

- Real projects
- Teams
- Mentors
- Sprints
- Tasks
- Reviews
- Feedback
- Evaluations
- Portfolio
- Career preparation

---

# 4. CORE PRODUCT PILLARS

## 4.1 Learning

مثل Udemy/Coursera ولكن مرتبط بالـCareer Journey.

Core:

```text
Course
 └── Section
      └── Lesson
           └── Progress
                └── Quiz
                     └── Completion
```

---

## 4.2 Internship

هو الـmain differentiator.

```text
Track
 → Assessment
 → Level
 → Team
 → Project
 → Backlog
 → Sprint
 → Task
 → Assignment
 → Development
 → Submission
 → Review
 → Feedback
 → Evaluation
```

---

## 4.3 Mentoring

Human mentoring:

```text
Mentor
 → Availability
 → Booking
 → Session
 → Feedback
```

AI Mentor يكون abstraction من البداية، والتنفيذ الكامل حسب قرار الـMVP.

---

# 5. BUSINESS MODEL

## 5.1 Customer Model

### `[DECIDED]`

الـMVP هو:

```text
Student = Paying Customer
Company = Future Partner
University = Potential Partner
```

لا يوجد Employer Portal كجزء من Core MVP.

---

# 6. PAYMENT MODEL

## 6.1 One-Time Purchase

### `[DECIDED]`

الطالب يدفع مرة واحدة مقابل Package.

ليس لدينا mandatory recurring subscription.

الطالب يستطيع:

- شراء Package
- العودة لاحقاً
- شراء Package أخرى
- الاحتفاظ بالـprevious enrollments
- الاحتفاظ بالـprogress
- الاحتفاظ بالـcertificates
- الاحتفاظ بالـassessments
- الاحتفاظ بالـevaluations

---

# 7. PACKAGE MODEL

Package ليست مجرد مدة.

الـPackage يجب أن تكون **Access + Entitlements + Journey Rules**.

## 7.1 Suggested Package Model

```text
Package
 ├── Duration
 ├── Price
 ├── Learning Access
 ├── Internship Access
 ├── Mentoring Entitlements
 ├── AI Entitlements
 ├── Assessment Policy
 ├── CV Policy
 ├── Internship Start Policy
 ├── Certificate Policy
 └── Career Services
```

---

# 8. INITIAL PACKAGE MATRIX

| Capability | 3 Months | 6 Months | 12 Months | Standalone |
|---|---|---|---|---|
| CV | Required | Required | Optional | N/A |
| AI Interview | Required | Required | Required | N/A |
| Learning | Yes | Yes | Yes | Future |
| Internship | Immediate | After preparation gate | TBD | No |
| Mentoring | TBD | TBD | TBD | Yes |
| AI Mentor | TBD | TBD | TBD | TBD |
| Certificate | TBD | TBD | TBD | TBD |
| Employer Recommendation | No/TBD | No/TBD | TBD | No |

---

# 9. PACKAGE ENTITLEMENTS

بدلاً من كتابة:

```csharp
if (package == ThreeMonths)
```

يفضل بناء entitlement-based model.

Examples:

```text
LearningAccess
InternshipAccess
MentoringCredits
AIInterviewAttempts
AIMentorAccess
CVParsing
CareerServices
Certificate
EmployerRecommendation
```

Suggested entities:

```text
Package
PackageEntitlement
EntitlementType
EntitlementValue
EnrollmentEntitlement
EntitlementUsage
```

---

## 9.1 Meeting Questions — Package Entitlements

- هل الـMentoring sessions Unlimited أم Credit-based؟
- هل كل Package لها عدد Sessions محدد؟
- هل الـAI Interview له عدد Attempts؟
- هل CV Parsing مرة واحدة أم يمكن إعادة التحليل؟
- هل الـunused mentoring credits تنتقل للـrenewal؟
- هل الـentitlements لها expiration مستقل؟
- ماذا يحدث للـentitlements عند Upgrade؟
- ماذا يحدث عند Renewal؟
- ماذا يحدث عند Refund؟
- هل Package يمكن أن تحتوي على Features إضافية مستقبلاً بدون تغيير الـdomain model؟

---

# 10. 3-MONTH JOURNEY

### `[DECIDED]`

الـ3 Months يجب أن يبدأ Internship مباشرة.

```text
Register
 ↓
Profile
 ↓
CV Required
 ↓
Track
 ↓
Package
 ↓
Payment
 ↓
Enrollment Activation
 ↓
AI Interview
 ↓
Level
 ↓
Team
 ↓
Internship
```

---

## 10.1 Questions

- هل الـ3 Months متاح للمبتدئين؟
- هل هناك minimum readiness score؟
- هل CV وحده كافٍ؟
- هل يمكن للطالب بدء Internship قبل ظهور نتيجة الـAI Interview؟
- هل Team Assignment ينتظر الـassessment؟
- ماذا يحدث إذا فشل الطالب في الـassessment؟
- هل يحصل على preparation path بدلاً من Internship؟
- هل يمكنه طلب إعادة assessment؟

---

# 11. 6-MONTH JOURNEY

CV Required.

```text
Register
 ↓
Profile
 ↓
CV
 ↓
Track
 ↓
Package
 ↓
Payment
 ↓
AI Interview
 ↓
Learning / Preparation
 ↓
Assessment
 ↓
Internship
 ↓
Mentoring
```

الـexact preparation duration ما زال `[OPEN]`.

---

## 11.1 Questions

- ما مدة الـPreparation؟
- هل الـinternship يبدأ بعد X weeks؟
- هل يجب إكمال Courses معينة؟
- هل توجد minimum skills؟
- هل Mentor يقرر readiness؟
- هل assessment واحد أم أكثر من assessment؟
- هل الطالب يمكن أن يبدأ Internship مبكراً إذا كان جاهزاً؟
- من يحدد readiness: Backend Rules أم Mentor أم AI؟
- هل الـpreparation gate configurable لكل Track؟

---

# 12. 12-MONTH JOURNEY

CV Optional.

```text
Register
 ↓
Profile
 ↓
CV OR Beginner
 ↓
Track
 ↓
Package
 ↓
Payment
 ↓
AI Interview
 ↓
Learning Foundation
 ↓
Mentoring
 ↓
Projects / Skills
 ↓
Internship
 ↓
Final Evaluation
 ↓
Career Readiness
 ↓
Potential Employer Recommendation
```

Employer recommendation ليست Job Guarantee.

---

## 12.1 Beginner Flow

```text
No CV
 ↓
Beginner Profile
 ↓
Track
 ↓
Package
 ↓
Payment
 ↓
Foundation Learning
 ↓
Assessments
 ↓
Mentoring
 ↓
Projects
 ↓
Internship
```

ممنوع اختراع خبرات أو Skills غير موجودة.

---

# 13. CV SYSTEM

## Rules

| Package | CV |
|---|---|
| 3 Months | Required |
| 6 Months | Required |
| 12 Months | Optional |

إذا CV موجود:

```text
Upload
 ↓
Store File
 ↓
Parse
 ↓
Extract Structured Data
 ↓
Populate Profile
 ↓
Student Confirmation
```

إذا 12-month بدون CV:

```text
"I don't have a CV / I'm a beginner"
```

يعتبر valid business state وليس error.

---

## 13.1 Suggested Data

```text
CV
 ├── FileId
 ├── StudentId
 ├── ParsingStatus
 ├── ParsedData
 ├── ParserVersion
 ├── CreatedAt
 └── UpdatedAt
```

---

## 13.2 Questions

- هل الطالب يستطيع رفع أكثر من CV؟
- أي CV هو active؟
- هل parsing يعيد كتابة profile مباشرة؟
- هل الطالب يراجع extracted data؟
- ماذا يحدث إذا parser فشل؟
- هل يستطيع retry؟
- هل AI يستطيع الوصول إلى CV؟
- هل Mentor يستطيع رؤية CV؟
- هل الطالب يستطيع حذف CV؟
- ما retention policy؟
- هل CV parsing مجاني أم entitlement؟
- هل 12-month beginner يحتاج profile fields إضافية؟

---

# 14. REGISTRATION & PROFILE

## Flow

```text
Register
 → Verify
 → Login
 → Create Profile
 → Track Selection
 → Package Selection
```

Profile may include:

- Personal information
- Education
- Skills
- Experience
- Projects
- GitHub/Portfolio
- CV
- Career goals
- Availability
- Preferred track

---

## Questions

- هل Email verification mandatory؟
- هل Phone verification؟
- هل social login في MVP؟
- هل user يستطيع تغيير email؟
- هل user يستطيع حذف account؟
- ما required profile fields؟
- هل profile completion شرط للدفع؟
- أم شرط للـenrollment activation؟
- هل profile changes بعد assessment تؤثر على assessment؟
- هل profile data versioned؟

---

# 15. TRACK SYSTEM

Track ليست Package.

```text
Track
 ├── Skills
 ├── Skill Matrix
 ├── Assessment Questions
 ├── Project Templates
 ├── Sprint Templates
 ├── Evaluation Criteria
 └── Requirements
```

Examples:

```text
Software Development
 ├── Backend
 │    └── ASP.NET
 ├── Frontend
 │    └── React
 └── Mobile
      └── Flutter
```

الـactual MVP tracks `[OPEN]`.

---

## 15.1 Track Change Policy

Suggested lifecycle:

```text
Before Payment
    → Free Change

After Payment / Before Assessment
    → Allowed with validation

After Assessment
    → Reassessment likely required

After Team Assignment
    → Admin approval

After Internship Starts
    → Locked by default
```

---

## Questions

- هل Track change قبل الدفع مفتوح؟
- بعد الدفع؟
- بعد assessment؟
- بعد team assignment؟
- بعد internship؟
- هل changing track يلغي assessment؟
- هل يلغي project؟
- هل course progress يتأثر؟
- هل يحتاج Admin approval؟
- هل student يستطيع شراء enrollments في Tracks مختلفة؟

---

# 16. AI INTERVIEW & ASSESSMENT

AI ليس صاحب القرار النهائي.

Architecture:

```text
AI Structured Result
        ↓
Backend Business Rules
        ↓
Final Level
        ↓
Eligibility
        ↓
Team Matching
```

---

## 16.1 Assessment Result

```text
AssessmentResult
 ├── SkillScores
 ├── OverallScore
 ├── Strengths
 ├── Weaknesses
 ├── SkillGaps
 ├── RecommendedLevel
 ├── Confidence
 ├── Model
 ├── PromptVersion
 └── CreatedAt
```

---

## 16.2 AI Abstractions

```text
IAIService
ICVParsingService
IAIAssessmentService
IAIInterviewService
ITeamMatchingService
IAIMentorService
```

---

## Questions

- كم Assessment Attempt؟
- هل Retake مسموح؟
- هل الـRetake overwrites result أم version جديدة؟
- هل student يستطيع Resume؟
- ماذا يحدث عند disconnect؟
- هل يوجد time limit؟
- هل questions randomized؟
- هل AI generates questions أم question bank؟
- هل AI-generated questions تحتاج review؟
- ماذا يحدث إذا AI provider down؟
- هل يوجد fallback rules؟
- هل يوجد human review؟
- هل AI score يمكن تغييره بواسطة Admin؟
- هل result لها expiration؟
- هل Renewal يحتاج assessment؟
- هل Upgrade يحتاج assessment؟
- كيف نضمن consistency؟
- هل نخزن model/prompt version؟

---

# 17. LEVEL SYSTEM

الـLevel taxonomy يجب أن يكون configurable.

Example:

```text
Beginner
Junior
Intermediate
Advanced
```

لكن القرار النهائي `[OPEN]`.

---

## Questions

- ما عدد الـlevels؟
- هل كل Track لها levels مختلفة؟
- ما scoring formula؟
- هل score ثابت؟
- هل skill gaps لها وزن؟
- هل AI recommendation يمكنها تغيير level؟
- هل Admin يستطيع override؟
- هل override يحتاج reason؟
- هل override يدخل في audit log؟

---

# 18. ENROLLMENT

Enrollment = student's actual purchased journey.

Suggested states:

```text
PendingPayment
Active
Preparing
TeamAssigned
InternshipActive
Completed
Cancelled
Expired
```

---

## Suggested Model

```text
Enrollment
 ├── StudentId
 ├── PackageId
 ├── TrackId
 ├── Status
 ├── StartDate
 ├── EndDate
 ├── CurrentLevel
 ├── AssessmentId
 └── CreatedAt
```

---

## Questions

- هل كل Purchase تعمل Enrollment واحدة؟
- هل الطالب يستطيع امتلاك أكثر من Active Enrollment؟
- هل two enrollments لنفس Track مسموحة؟
- هل enrollments يمكن أن تعمل concurrently؟
- هل enrollment جديدة توقف القديمة؟
- هل student يحتفظ بالـprevious package access؟
- ماذا يحدث عند expiry أثناء Internship؟
- هل team/chat تستمر بعد expiry؟
- هل admin يستطيع Reactivate؟
- هل Enrollment قابلة للتحويل لمستخدم آخر؟
- هل Pause مسموح؟
- هل Progress يتجمد؟
- هل Mentor/Team assignment تتجمد؟

---

# 19. PACKAGE RENEWAL

هذه نقطة أساسية ويجب حسمها في الـmeeting.

## Possible Models

### Option A — New Purchase

```text
Old Enrollment
     +
New Order
     ↓
New Enrollment
```

Advantages:
- clean history
- easier accounting
- clear lifecycle
- no mutation of old package

### Option B — Extension

```text
Existing Enrollment
      ↓
Renewal Transaction
      ↓
EndDate += Duration
```

Advantages:
- continuity
- simpler student experience

### Recommended

`Option A` غالباً أفضل للـaudit/history، مع إمكانية ربط enrollments ببعضها:

```text
PreviousEnrollmentId
RenewalOfEnrollmentId
```

---

## Renewal Questions

- هل الطالب يستطيع renew وهو Active؟
- هل renewal early مسموح؟
- هل renewal بعد Expiry مسموح؟
- هل renewal بعد Completion مسموح؟
- هل renewal نفس Package فقط؟
- هل يمكن 3 → 6؟
- هل يمكن 6 → 12؟
- هل يمكن 12 → 12؟
- هل Track تظل كما هي؟
- هل Renewal تحتاج assessment جديد؟
- هل progress يتصفر؟
- هل Team تستمر؟
- هل Project يستمر؟
- هل Internship time يزيد؟
- هل Renewal تعمل Enrollment جديدة أم Extension؟
- ماذا لو السعر تغير؟
- هل يوجد Renewal discount؟
- هل unused time يتحسب؟
- هل يحتاج Terms acceptance جديد؟
- ماذا يحدث إذا الدفع فشل؟
- ماذا يحدث لو payment نجح لكن renewal processing فشل؟

---

# 20. UPGRADE / DOWNGRADE

## Upgrade

Examples:

```text
3M → 6M
6M → 12M
3M → 12M
```

## Downgrade

Examples:

```text
12M → 6M
6M → 3M
```

---

## Recommended MVP Rule

### `[RECOMMENDED]`

Upgrade ممكن، Downgrade يؤجل إلى بعد MVP إلا إذا business requires it.

Upgrade should create:

```text
Upgrade Order
 ↓
Payment
 ↓
Validation
 ↓
Entitlement Change
 ↓
Enrollment Transition
```

---

## Questions

- هل 3M → 6M مسموح؟
- هل 6M → 12M؟
- هل 12M → 6M؟
- هل downgrade مسموح؟
- هل upgrade فقط قبل Internship؟
- هل upgrade بعد Internship يبدأ؟
- كيف نحسب price difference؟
- هل نستخدم unused time credit؟
- هل upgrade فوري؟
- هل يحتاج reassessment؟
- هل Team تتغير؟
- هل Project يتغير؟
- هل progress يظل؟
- هل certificate يتأثر؟
- هل Track يمكن تغييرها مع upgrade؟
- ماذا يحدث إذا upgrade payment failed؟
- ماذا يحدث إذا payment succeeded but activation failed؟
- هل توجد upgrade discount rules؟

---

# 21. STANDALONE MENTORING SESSION

هذه يجب أن تكون Purchase مستقلة عن Package.

## Suggested Model

```text
MentoringProduct
 ├── Duration
 ├── Topic/Category
 ├── Price
 └── Rules

Order
 ↓
Payment
 ↓
MentoringCredit
 ↓
Booking
 ↓
Session
```

---

## Example

طالب عنده Package ويريد Session إضافية:

```text
Active Enrollment
      +
Standalone Session Purchase
      ↓
Mentoring Credit
      ↓
Book Mentor
```

---

## Questions

- هل أي user يقدر يشتري Session؟
- هل لازم يكون enrolled؟
- هل active students يستطيعون شراء extra sessions؟
- هل session مرتبطة بـTrack؟
- هل session مرتبطة بـMentor؟
- هل student يختار mentor؟
- هل mentor يحدد سعره؟
- هل السعر حسب duration؟
- هل duration 30/45/60 minutes؟
- هل credits expiry؟
- هل unused credit rollover؟
- هل Session قابلة للنقل؟
- هل Session لها refund؟
- Cancellation policy؟
- Reschedule policy؟
- Student no-show؟
- Mentor no-show؟
- هل booking confirmation تعمل Order؟
- هل Session لها meeting link؟
- هل recording موجود؟
- من يقدر يشوف recording؟
- كم مدة الاحتفاظ بالتسجيل؟
- هل توجد Session notes؟
- هل يوجد rating؟
- هل session تدخل في student's career history؟

---

# 22. PRODUCT / OFFER ABSTRACTION

إذا المنصة ستبيع:

- Packages
- Mentoring Sessions
- Future Courses
- Future Career Services

فالأفضل ألا يكون الـOrder مرتبطاً مباشرةً بـPackage فقط.

Suggested:

```text
Product / Offer
     ↓
Order
 ├── OrderItem
 │     ├── Package
 │     ├── MentoringSession
 │     └── Future Products
```

مع الاحتفاظ بـ`PriceSnapshot`.

---

# 23. ORDER MODEL

```text
Order
 ├── Id
 ├── StudentId
 ├── Status
 ├── Currency
 ├── Total
 ├── CreatedAt
 └── Items

OrderItem
 ├── ProductType
 ├── ProductId
 ├── Quantity
 ├── UnitPrice
 ├── Discount
 └── PriceSnapshot
```

---

# 24. PAYMENT SYSTEM

Core flow:

```text
Product
 ↓
Order
 ↓
Payment
 ↓
Provider
 ↓
Webhook
 ↓
Verify
 ↓
Activate
```

**Client-side success page لا تكفي لتفعيل Enrollment.**

---

## Payment Requirements

- Idempotency
- Webhook verification
- Provider transaction ID
- Internal transaction ID
- Payment state
- Retry
- Reconciliation
- Refund
- Audit
- Secure configuration

---

## Questions

- ما Payment Gateway في مصر؟
- Currency؟
- هل VAT/Tax موجود؟
- هل Invoice مطلوب؟
- هل Promo Codes؟
- هل Discounts؟
- هل Installments؟
- ماذا لو payment succeeds والـwebhook متأخر؟
- ماذا لو webhook duplicate؟
- ماذا لو client says success والbackend لم يؤكد؟
- ماذا لو amount مختلف؟
- ماذا لو order expired؟
- هل retry payment على نفس Order؟
- هل يمكن دفع نفس Order مرتين؟
- كيف نمنع duplicate activation؟
- Partial refund؟
- Full refund؟
- Chargeback؟
- Reconciliation process؟
- من يملك financial permissions؟

---

# 25. REFUND / CANCELLATION

Policy يجب أن تكون business decision.

Possible rules:

```text
Before activation → Full refund
After activation → Conditional
After significant usage → No/Partial refund
```

لكن هذا مجرد recommendation.

---

## Questions

- هل يمكن إلغاء package؟
- خلال كم ساعة/يوم؟
- هل بعد بدء Internship؟
- هل بعد استخدام Course؟
- هل بعد استخدام Session؟
- هل بعد Assessment؟
- هل refund كامل؟
- Partial refund؟
- هل transaction fees تُخصم؟
- ماذا يحدث للـEnrollment؟
- ماذا يحدث للـcertificate؟
- ماذا يحدث للـteam؟
- ماذا يحدث للـchat؟
- ماذا يحدث للـfiles؟
- ماذا يحدث للـcredits؟

---

# 26. PAUSE / FREEZE

Feature تحتاج قراراً واضحاً.

Possible:

```text
Active
 ↓
Paused
 ↓
Resumed
```

---

## Questions

- هل pause مسموح؟
- كم مرة؟
- maximum duration؟
- هل EndDate يتم تمديده؟
- هل Internship pauses؟
- هل Team تستمر؟
- هل Mentor تستمر؟
- هل Tasks تتوقف؟
- هل Chat يتوقف؟
- هل credits تتوقف؟
- هل Admin يستطيع force pause؟
- هل medical/emergency/business reasons لها policies مختلفة؟

---

# 27. TEAM FORMATION

AI-assisted, not AI-only.

Flow:

```text
Eligible Students
 ↓
Business Constraints
 ↓
Compatibility Analysis
 ↓
AI Recommendation
 ↓
Backend Rules
 ↓
Admin Approval
 ↓
Team Created
```

Factors:

- Track
- Level
- Skills
- Skill Gaps
- Project Requirements
- Availability
- Team Capacity
- Mentor Availability
- Compatibility

---

## Team Model

```text
Team
 ├── Track
 ├── Project
 ├── Capacity
 ├── Status
 └── Members
```

Team size configurable.

---

## Questions

- ماذا لو لا يوجد عدد كافٍ؟
- ماذا لو عدد الطلاب كبير؟
- هل team incomplete مسموحة؟
- هل team size ثابت أم configurable؟
- ماذا لو Mentor unavailable؟
- هل student يطلب team change؟
- هل Admin يستطيع نقل student؟
- ماذا يحدث للـtasks؟
- ماذا يحدث للـperformance history؟
- هل team merge/split مسموح؟
- هل team size يتغير أثناء project؟
- ماذا لو Skill مهمة غير موجودة؟
- هل AI recommendation قابلة للoverride؟
- هل يجب إظهار سبب الـmatching؟

---

# 28. MENTOR ASSIGNMENT

Technical model يمكن أن يدعم multiple mentors.

Operational recommendation:

```text
1 Primary Mentor
+
Optional Supporting Mentors
```

---

## Questions

- هل Mentor واحد لكل Team؟
- هل Mentor متعدد؟
- هل mentor assignment تلقائي؟
- هل admin assignment؟
- هل mentor capacity لها limit؟
- ماذا يحدث عند mentor absence؟
- هل students يمكنهم طلب mentor؟
- هل mentor يرى كل student data؟
- هل mentor يستطيع تغيير level؟
- هل mentor evaluation تؤثر على final score؟

---

# 29. INTERNSHIP ENGINE

يجب بناء Generic Internship Engine وليس hardcoded workflow.

```text
Project
 ↓
Backlog
 ↓
Sprint
 ↓
Tasks
 ↓
Assignments
 ↓
Submission
 ↓
Review
 ↓
Feedback
 ↓
Evaluation
```

---

# 30. PROJECT TEMPLATE SYSTEM

### `[RECOMMENDED]`

Track-driven templates:

```text
Track
 ↓
ProjectTemplate
 ↓
BacklogTemplate
 ↓
SprintTemplate
 ↓
TaskTemplate
```

Admin يستطيع override.

---

## Questions

- هل project Admin-created؟
- أم Track template-driven؟
- هل team تستطيع اختيار project؟
- هل project يتغير بعد البدء؟
- ماذا يحدث إذا project cancelled؟
- هل project reusable؟
- هل projects لها versions؟
- هل template لها owner؟
- هل tasks تتولد تلقائياً؟

---

# 31. SPRINT

Suggested:

```text
Sprint
 ├── Goal
 ├── StartDate
 ├── EndDate
 ├── Status
 ├── Tasks
 └── Evaluation
```

Task statuses:

```text
Todo
InProgress
Review
Done
Rejected
```

---

## Questions

- هل Sprint dates fixed؟
- هل mentor يستطيع extend؟
- هل Admin يستطيع extend؟
- هل student يعمل ahead؟
- ماذا يحدث عند missed sprint؟
- هل rejected task يرجع InProgress؟
- هل Done task يمكن reopen؟
- هل due date قابلة للتغيير؟
- هل sprint score يدخل في final evaluation؟

---

# 32. TASK MANAGEMENT

Jira-like لكن ليس Jira clone.

Task:

```text
Task
 ├── Title
 ├── Description
 ├── Assignee
 ├── Status
 ├── Priority
 ├── Sprint
 ├── DueDate
 ├── Skill
 └── Attachments
```

---

## Questions

- من يستطيع create task؟
- هل student يستطيع create task؟
- هل assignment لشخص واحد أم multiple؟
- هل task points موجودة؟
- هل priority؟
- هل labels؟
- هل dependencies؟
- هل task comments؟
- هل task history/audit؟
- هل mentor يستطيع reassign؟
- ماذا يحدث إذا member ترك team؟

---

# 33. SUBMISSION / REVIEW

Flow:

```text
Task
 ↓
Submission
 ↓
Review
 ↓
Approve / Reject
 ↓
Feedback
 ↓
Task Completion
```

---

## Questions

- هل submission واحدة أم multiple؟
- هل كل rejection يحتاج feedback؟
- هل mentor يستطيع approve مباشرة؟
- هل Admin يستطيع override؟
- هل final submission versioned؟
- هل student يستطيع تعديل بعد submission؟
- هل review SLA؟
- هل attachments stored in object storage؟

---

# 34. FINAL EVALUATION

Possible dimensions:

```text
Technical Skills
Task Performance
Sprint Performance
Project Quality
Teamwork
Communication
Mentor Evaluation
Assessment
Learning Progress
```

Formula `[OPEN]`.

---

## Questions

- ما weights؟
- هل AI يدخل في final score؟
- هل mentor score يدخل؟
- هل attendance؟
- هل task completion؟
- هل code quality؟
- هل peer evaluation؟
- هل final assessment؟
- هل student يستطيع appeal؟
- هل Admin override؟
- هل final score versioned؟

---

# 35. LEARNING SYSTEM

Core:

```text
Course
 ↓
Section
 ↓
Lesson
 ↓
Progress
 ↓
Quiz
 ↓
Completion
```

---

# 36. SKILL GAP → LEARNING

ميزة مهمة:

```text
Assessment
 ↓
Missing Skill
 ↓
Recommended Course/Lesson
 ↓
Learning
 ↓
Skill Improvement
```

Recommendation engine يمكن أن يبدأ Rule-Based.

---

## Questions

- هل student يستطيع access all courses؟
- أم package-based؟
- هل standalone courses في MVP؟
- هل course progress ينتقل بين enrollments؟
- ماذا يحدث بعد refund؟
- هل lesson download؟
- هل quiz attempts limited؟
- هل course completion prerequisite للInternship؟
- هل skill gaps recommendations mandatory؟
- هل Admin يستطيع override recommendation؟

---

# 37. MENTORING SYSTEM

Core:

```text
Mentor
 ↓
Availability
 ↓
Booking
 ↓
Session
 ↓
Feedback
```

---

## Questions

- هل sessions included؟
- كم session لكل Package؟
- duration؟
- booking window؟
- cancellation؟
- reschedule؟
- no-show؟
- mentor selection؟
- auto assignment؟
- notes؟
- rating؟
- time zones؟
- ماذا لو booking race condition؟
- هل booking transactionally locks slot؟

---

# 38. AI MENTOR

### `[OPEN]`

### Option A
Full AI Mentor in MVP.

### Option B — Recommended
Build abstraction now:

```text
IAIMentorService
```

لكن full AI Mentor Phase 2.

Reason:
- يقلل MVP scope
- يسمح بإضافة AI لاحقاً
- لا يكسر architecture
- AI Interview وCV Parsing يظلوا Core

---

# 39. MESSAGING

MVP:

```text
Team Chat
Direct Chat
Student ↔ Mentor
Mentor ↔ Student
```

Architecture:

```text
SignalR
 +
SQL Server persistence
```

At scale:
- scale-out/backplane
- or managed realtime infrastructure

---

## Questions

- من يستطيع message من؟
- هل students يقدروا يكلموا خارج team؟
- هل former mentor يستطيع messaging؟
- ماذا يحدث بعد expiry؟
- message retention؟
- attachments؟
- moderation؟
- report/block؟
- unread count؟
- notification preferences؟
- هل messages قابلة للحذف؟

---

# 40. NOTIFICATIONS

MVP:

- In-App
- Email

Events:

```text
PaymentCompleted
EnrollmentActivated
CVParsed
AssessmentAvailable
AssessmentCompleted
TeamAssigned
SprintStarted
TaskAssigned
TaskReviewed
MentoringBooked
NewMessage
CourseCompleted
InternshipCompleted
CertificateIssued
```

Push `[PHASE 2]`.

---

## Questions

- ما notification channels؟
- هل user يستطيع disable email؟
- هل critical notifications لا يمكن disable؟
- هل notifications لها priority؟
- هل duplicate events ممكن؟
- هل retry؟
- هل notification templates versioned؟
- هل scheduled reminders؟

---

# 41. CERTIFICATES

Trigger `[OPEN]`.

### Option A
Certificate on package completion.

### Option B
Certificate on internship completion + evaluation.

### Recommended
Certificate should represent meaningful achievement, not just payment duration.

---

## Questions

- ما trigger؟
- هل 3/6/12 لها certificates مختلفة؟
- هل Renewal يحصل على certificate؟
- هل Upgrade يحصل على certificate جديد؟
- هل certificate Track-specific؟
- هل Certificate ID؟
- هل public verification؟
- هل Admin revoke؟
- ماذا يحدث بعد refund؟

---

# 42. EMPLOYER RECOMMENDATION

خصوصاً 12-month.

ليست:

> Job Guarantee

بل:

> Candidate Recommendation / Referral

Possible eligibility:

```text
Learning Completion
+
Technical Assessment
+
Internship Completion
+
Project Performance
+
Sprint Performance
+
Mentor Evaluation
+
Final Evaluation
+
CV/Profile/Portfolio
```

---

## Questions

- هل Employer Recommendation داخل MVP؟
- هل 12-month فقط؟
- minimum score؟
- internship completion required؟
- mentor score threshold؟
- portfolio required؟
- student opt-in؟
- consent؟
- ما data التي يتم مشاركتها؟
- مع كم Company؟
- automatic أم admin reviewed؟
- هل company تستطيع reject؟
- هل interview guaranteed؟
- Job guaranteed؟ **No**
- كيف نقيس success؟

---

# 43. ADMIN & OPERATIONS

Admin capabilities:

- Students
- Mentors
- Tracks
- Skills
- Packages
- Courses
- Projects
- Teams
- Assessments
- Payments
- Enrollments
- Overrides
- Audit logs

---

# 44. ADMIN ROLES

Suggested:

```text
SuperAdmin
OperationsAdmin
FinanceAdmin
ContentAdmin
MentorManager
SupportAdmin
```

لكن final roles `[OPEN]`.

---

## Questions

- من يستطيع تغيير Package price؟
- من يستطيع Refund؟
- من يستطيع change Track؟
- من يستطيع change Level؟
- من يستطيع move Team؟
- من يستطيع manually activate Enrollment؟
- من يستطيع edit Payment؟
- هل كل override يحتاج reason؟
- هل كل override audit logged؟
- هل Finance منفصل؟
- هل Admin يرى CV؟
- هل Admin يستطيع access private files؟

---

# 45. AUDIT LOG

أي business-critical mutation يجب أن تكون auditable.

Examples:

```text
EnrollmentActivated
EnrollmentPaused
EnrollmentResumed
PackageUpgraded
PackageRenewed
PaymentRefunded
TrackChanged
LevelOverridden
TeamChanged
AssessmentOverridden
CertificateRevoked
```

---

# 46. FILE STORAGE

Large files لا تخزن داخل SQL Server.

Architecture:

```text
SQL Server
    ↓
Metadata

Object Storage
    ↓
Actual File
```

Files:

- CV
- Videos
- PDFs
- Attachments
- Certificates
- Project files

Metadata:

```text
File
 ├── Id
 ├── OwnerId
 ├── FileName
 ├── ContentType
 ├── Size
 ├── StorageKey
 ├── Status
 └── CreatedAt
```

---

## Questions

- ما Object Storage؟
- max file size؟
- allowed MIME types؟
- antivirus scanning؟
- signed URLs؟
- expiration؟
- access control؟
- public/private؟
- backup؟
- retention؟
- deletion policy؟

---

# 47. TECHNICAL ARCHITECTURE

## Recommended

```text
React / TypeScript
        ↓
ASP.NET Core API
        ↓
Modular Monolith
        ↓
Application
        ↓
Domain
        ↓
Infrastructure
        ↓
SQL Server / Object Storage / External Providers
```

لا نبدأ Microservices لمجرد الـscalability.

---

# 48. CLEAN ARCHITECTURE

Suggested:

```text
src/
  API/

  Modules/
    Identity/
    Students/
    Tracks/
    Packages/
    Enrollment/
    Payments/
    Assessment/
    AI/
    Internship/
    Learning/
    Mentoring/
    Messaging/
    Notifications/
    Administration/

  BuildingBlocks/
```

Dependency:

```text
Presentation
      ↓
Application
      ↓
Domain

Infrastructure
      ↓
Application / Domain
```

---

# 49. DOMAIN MODULES

Each module should own its business rules.

Examples:

```text
Packages
    Package
    PackageEntitlement

Payments
    Order
    OrderItem
    Payment
    Refund

Enrollment
    Enrollment
    EnrollmentTransition
    Renewal
    Upgrade

Assessment
    Assessment
    Attempt
    Answer
    Result

Internship
    Team
    Project
    Sprint
    Task
    Submission
    Review
    Evaluation
```

---

# 50. DATABASE PRINCIPLES

SQL Server:

- Proper relational model
- Foreign keys
- Constraints
- Indexes
- Transactions
- Concurrency handling
- Pagination
- Projection
- No N+1
- No unbounded collection queries
- Query optimization
- Auditability

Read-only queries:

```csharp
AsNoTracking()
```

when appropriate.

---

# 51. IMPORTANT DATABASE ENTITIES

Core:

```text
User
StudentProfile
MentorProfile

Track
Skill
SubCategory
TrackSkill

Package
PackageEntitlement

Order
OrderItem
Payment
Refund
Discount
PriceSnapshot

Enrollment
EnrollmentTransition

CV
Assessment
AssessmentAttempt
AssessmentAnswer
AssessmentResult

Team
TeamMember
Project
ProjectTemplate
Sprint
Task
TaskAssignment
Submission
Review
Evaluation

Course
Section
Lesson
LessonProgress
Quiz
QuizAttempt

Mentor
MentorAvailability
MentoringProduct
MentoringCredit
MentoringBooking
MentoringSession

Conversation
ConversationMember
Message

Notification

Certificate

AuditLog

AnalyticsEvent
```

ليس شرطاً تنفيذ كل entity في Sprint 0؛ يتم إدخالها حسب module dependency.

---

# 52. API DESIGN

REST API.

Examples:

```text
POST /api/auth/register
POST /api/auth/login

GET /api/tracks
GET /api/tracks/{id}

GET /api/packages
GET /api/packages/{id}

POST /api/orders
POST /api/payments
POST /api/payments/webhook

GET /api/enrollments
GET /api/enrollments/{id}

POST /api/assessments/{id}/start
POST /api/assessments/{id}/answers
POST /api/assessments/{id}/submit

GET /api/teams/{id}
GET /api/projects/{id}
GET /api/sprints/{id}

POST /api/tasks/{id}/submit
POST /api/submissions/{id}/review

GET /api/courses
GET /api/courses/{id}

GET /api/mentors
POST /api/mentoring/bookings

GET /api/messages
```

Collections يجب أن تكون paginated.

---

# 53. API REQUIREMENTS

- Authentication
- Authorization
- Validation
- Consistent errors
- Correlation ID
- Rate limiting
- Pagination
- Filtering
- Sorting
- Idempotency where needed
- Versioning strategy
- Secure file access
- Audit for critical operations

---

# 54. FRONTEND ARCHITECTURE

React + TypeScript.

Suggested:

```text
src/
  app/
  features/
    auth/
    profile/
    tracks/
    packages/
    checkout/
    enrollment/
    assessment/
    internship/
    learning/
    mentoring/
    messaging/
    notifications/
    admin/
  shared/
    components/
    hooks/
    api/
    types/
    utils/
```

---

# 55. FRONTEND REQUIREMENTS

Every major page needs:

- Loading state
- Error state
- Empty state
- Success state
- Validation
- Responsive design
- Permission-aware UI
- API error handling

Critical screens:

```text
Landing
Register
Login
Profile
CV
Track Selection
Package Selection
Checkout
Payment Result
Assessment
Assessment Result
Student Dashboard
Team
Project
Sprint
Task
Course
Mentoring
Messages
Notifications
Admin
```

---

# 56. SECURITY

Core:

- Authentication
- Authorization
- Resource-level authorization
- Input validation
- Secure file access
- Secret management
- Rate limiting
- Audit logs
- Secure cookies/tokens
- CORS
- CSRF strategy where applicable
- Password security
- Session management
- Encryption in transit
- Sensitive data protection

---

## Questions

- من يستطيع رؤية CV؟
- هل AI يستطيع الوصول إلى CV؟
- هل Mentor يستطيع رؤية CV؟
- هل Student يستطيع delete CV؟
- Account deletion؟
- Data retention؟
- AI processing consent؟
- Employer sharing consent؟
- PII encryption؟
- Audit access؟
- Signed URLs؟
- Data export؟
- Privacy requirements؟

---

# 57. SCALABILITY TARGET

Target:

> Hundreds of thousands of students.

Architecture should support:

```text
Horizontal API Scaling
+
SQL Optimization
+
Background Workers
+
Object Storage
+
Caching where justified
+
Realtime Scale-Out
+
Observability
```

لا يعني ذلك أننا نبدأ Microservices.

---

# 58. SCALE REQUIREMENTS

Mandatory:

- Pagination
- Indexing
- Projection
- No N+1
- Async processing
- Background jobs
- Queue
- Idempotent jobs
- Retry
- Health checks
- Monitoring
- Load testing
- Stress testing
- Connection pooling
- Rate limiting
- Object storage
- SignalR scale-out plan

---

## Questions

- ما expected concurrent users؟
- Peak traffic؟
- Peak assessment users؟
- Peak payment callbacks؟
- AI provider quotas؟
- CV upload peak؟
- DB size after 1 year؟
- SignalR connections؟
- Object storage growth؟
- RPO؟
- RTO؟
- Backup retention؟
- Autoscaling؟
- Cost ceiling؟

---

# 59. BACKGROUND PROCESSING

Do not perform expensive work inside HTTP request when unnecessary.

Examples:

```text
CV Parsing
AI Assessment
Email
Notifications
Analytics Processing
Report Generation
Certificate Generation
File Processing
```

Flow:

```text
API
 ↓
Persist Job
 ↓
Queue
 ↓
Worker
 ↓
Process
 ↓
Retry / Failure
```

Need:

- Idempotency
- Retry
- Failure state
- Monitoring
- Dead-letter/recovery strategy where applicable

---

# 60. CACHING

Cache only where justified.

Potential:

```text
Track Catalog
Package Catalog
Course Catalog
Static Configuration
```

Do not cache business state blindly.

Potential Redis later/when justified.

---

# 61. SIGNALR

Use SignalR for:

- Team Chat
- Direct Chat
- Notifications
- Realtime task updates if needed

Persistence remains in database.

At scale:

```text
Multiple API Instances
        ↓
SignalR Scale-Out
```

---

# 62. AI ARCHITECTURE

Provider-agnostic.

```text
Application
   ↓
IAIService
   ↓
AI Provider
```

AI must have:

- Timeout
- Retry where safe
- Structured output
- Validation
- Versioning
- Logging
- Cost monitoring
- Failure fallback

---

# 63. AI FAILURE POLICY

If AI fails:

```text
AI Failed
 ↓
Do NOT corrupt Enrollment
 ↓
Keep Assessment state recoverable
 ↓
Retry / fallback
 ↓
Human/Admin fallback if required
```

AI should not be a single point of failure for critical business state.

---

# 64. DATA & ANALYTICS

Events from day one:

```text
UserRegistered
ProfileCompleted
CVUploaded
CVParsed
TrackSelected
PackageSelected
PaymentStarted
PaymentCompleted
EnrollmentActivated
AssessmentStarted
AssessmentCompleted
LevelDetermined
TeamAssigned
CourseStarted
LessonCompleted
QuizCompleted
SprintStarted
TaskAssigned
TaskCompleted
TaskSubmitted
TaskReviewed
MentoringBooked
InternshipCompleted
CertificateIssued
```

---

# 65. KPIs

Business:

- Registration Conversion
- Profile Completion
- CV Completion
- Payment Conversion
- Enrollment Rate
- Renewal Rate
- Upgrade Rate
- Standalone Session Sales
- Revenue
- Refund Rate
- Dropout Rate

Learning:

- Course Completion
- Quiz Completion
- Skill Improvement

Internship:

- Team Assignment Time
- Sprint Completion
- Task Completion
- Project Completion
- Internship Completion

Career:

- Readiness
- Employer Recommendations
- Interview Rate
- Placement metrics when available

---

# 66. ANALYTICS QUESTIONS

- ما mandatory events؟
- من يملك KPI definitions؟
- كيف نمنع duplicate events؟
- Event versioning؟
- Anonymous events؟
- Consent؟
- Funnel definitions؟
- Revenue definition؟
- Renewal metric؟
- Upgrade metric؟
- Churn؟
- Dropout؟
- Session conversion؟

---

# 67. QA STRATEGY

QA يبدأ من Sprint 0.

Flow:

```text
Requirement
 ↓
Acceptance Criteria
 ↓
Test Cases
 ↓
Implementation
 ↓
Unit Test
 ↓
Integration Test
 ↓
API Test
 ↓
E2E
 ↓
Performance
 ↓
Security
 ↓
UAT
```

---

# 68. CRITICAL E2E TESTS

## Purchase

```text
Register
 → Profile
 → Track
 → Package
 → Payment
 → Enrollment
```

## Assessment

```text
Enrollment
 → Interview
 → Answers
 → AI Evaluation
 → Backend Rules
 → Level
```

## Internship

```text
Team
 → Project
 → Sprint
 → Task
 → Submission
 → Review
 → Feedback
 → Evaluation
```

---

# 69. PAYMENT TEST CASES

Mandatory:

- Successful payment
- Failed payment
- Pending payment
- Duplicate webhook
- Delayed webhook
- Invalid webhook
- Amount mismatch
- Expired order
- Retry
- Double payment
- Refund
- Partial refund
- Provider timeout
- Provider unavailable

---

# 70. QA QUESTIONS

- ما automation coverage target؟
- ما critical paths؟
- هل API integration tests mandatory؟
- هل E2E قبل release؟
- هل load testing قبل MVP؟
- هل security testing؟
- هل regression suite؟
- من يملك UAT؟
- ما release blocking bugs؟

---

# 71. DEVOPS

Environments:

```text
Development
Staging
Production
```

CI/CD:

```text
Commit
 ↓
Build
 ↓
Unit Tests
 ↓
Integration Tests
 ↓
Security Checks
 ↓
Artifact
 ↓
Deploy
```

---

# 72. OBSERVABILITY

Need:

- Structured logs
- Correlation IDs
- Error tracking
- Metrics
- Health checks
- DB monitoring
- Background job monitoring
- AI latency/failure monitoring
- Payment monitoring
- Alerts

---

# 73. BACKUPS / RECOVERY

Need:

- SQL backups
- Retention policy
- Restore tests
- Object storage backup/versioning
- Recovery procedures
- RPO
- RTO

---

# 74. TEAM WORKSTREAMS

## Product / Business

Responsibilities:

- Scope
- Business rules
- Package definitions
- Pricing
- Eligibility
- Journeys
- Acceptance Criteria
- KPIs
- Policies

---

## UI/UX

- Design system
- User journeys
- Wireframes
- High fidelity
- Prototype
- Responsive design
- UX validation
- Empty/loading/error states

---

## Backend

- Clean Architecture
- Domain
- Database
- APIs
- Authentication
- Authorization
- Payments
- Enrollment
- AI integration
- Internship engine
- Learning
- Mentoring
- Messaging
- Notifications
- Infrastructure

---

## Frontend

- React
- TypeScript
- Routing
- Auth
- API integration
- State management
- Forms
- Dashboard
- Internship UI
- Learning UI
- Mentoring
- Messaging
- Admin

---

## AI

- CV Parsing
- AI Interview
- Assessment
- AI Matching
- AI Mentor abstraction
- Evaluation
- Model monitoring
- Prompt/version management

---

## Data

- Event schema
- Data quality
- KPIs
- Dashboards
- Analytics

---

## QA

- Test strategy
- Test cases
- Automation
- Regression
- E2E
- Performance
- Security
- UAT

---

## DevOps

- Environments
- CI/CD
- Deployment
- Monitoring
- Backups
- Scaling
- Security
- Recovery

---

# 75. SPRINT 0 — FOUNDATION

## Goal

Freeze scope and establish technical foundation.

### Product

- Freeze MVP scope
- Actors
- Journeys
- Package rules
- CV rules
- Track rules
- Acceptance Criteria
- Open Decisions

### Backend

- .NET solution
- Clean Architecture
- Module boundaries
- SQL Server
- EF Core
- Identity/Auth
- Error handling
- Validation
- Configuration
- Logging
- CI/CD foundation

### Frontend

- React + TypeScript
- Routing
- API client
- Auth shell
- Design system integration

### AI

- `IAIService`
- CV parsing contract
- Assessment contract
- AI interview contract

### QA

- Test strategy
- Critical E2E
- Environments

### DevOps

- Dev/Staging
- Initial CI/CD
- Secrets
- Logging

### Acceptance

- Solution builds
- API starts
- DB connects
- Auth foundation works
- CI pipeline runs
- Architecture boundaries established

### Meeting Questions

- هل architecture final؟
- هل MVP scope frozen؟
- هل package rules frozen؟
- هل payment provider selected؟
- هل tracks selected؟
- هل level model selected؟

---

# 76. SPRINT 1 — IDENTITY & PROFILE

### Backend

- Registration
- Login
- User
- Student
- Profile
- Roles
- Permissions
- CV metadata
- CV upload

### Frontend

- Register
- Login
- Profile
- CV upload
- Required/Optional UX

### AI

- CV Parsing POC

### QA

- Auth
- Access
- Profile
- CV permissions

### Acceptance

```text
Register
 → Login
 → Profile
 → CV
```

### Questions

- Email verification؟
- Phone verification؟
- CV multiple versions؟
- Profile required fields؟
- Account deletion؟

---

# 77. SPRINT 2 — TRACKS & PACKAGES

### Backend

- Track
- Skill
- TrackSkill
- Package
- PackageEntitlement
- Eligibility Rules

### Frontend

- Track catalog
- Track details
- Package catalog
- Package details
- Eligibility UI

### QA

- 3M CV required
- 6M CV required
- 12M CV optional

### Acceptance

Student can:

```text
Browse Track
 → Select Track
 → View Package
 → Understand Entitlements
```

### Questions

- Pricing model؟
- Track + Package pricing؟
- Package fixed price؟
- Entitlements final؟

---

# 78. SPRINT 3 — CHECKOUT / PAYMENT / ENROLLMENT

### Backend

- Product/Offer
- Order
- OrderItem
- Payment
- Webhook
- Refund foundation
- Enrollment
- Enrollment state machine
- Idempotency

### Frontend

- Checkout
- Payment status
- Success/failure/pending

### QA

- Payment scenarios
- Duplicate webhook
- Retry
- Failed activation

### Acceptance

```text
Verified successful payment
        ↓
Exactly one valid Enrollment
```

### Questions

- Gateway؟
- Refund policy؟
- Package duration starts when؟
- Order expiration؟
- Promo codes؟

---

# 79. SPRINT 4 — ASSESSMENT / AI INTERVIEW

### Backend

- Assessment
- Question bank
- Attempts
- Answers
- Results
- Levels
- State machine

### AI

- CV context
- Track context
- Interview
- Structured evaluation
- Confidence
- Versioning

### Frontend

- Interview UI
- Progress
- Result

### QA

- Resume
- Retry
- AI failure
- Invalid AI output
- Result persistence

### Acceptance

```text
Enrollment
 → Assessment
 → AI Result
 → Backend Decision
 → Level
```

### Questions

- Attempts؟
- Retake؟
- Human fallback؟
- AI-generated questions؟
- Score formula؟

---

# 80. SPRINT 5 — LEVEL & TEAM FORMATION

### Backend

- Level rules
- Eligibility
- Team
- Team members
- Mentor assignment
- Constraints
- Admin override

### AI

- Compatibility recommendation

### Frontend

- Assessment result
- Team status
- Team dashboard

### Admin

- Manual assignment
- Override

### Acceptance

```text
Paid
 → Assessed
 → Level
 → Valid Team
```

### Questions

- Team size؟
- Incomplete team؟
- Student team change؟
- Mentor capacity؟
- AI override؟

---

# 81. SPRINT 6 — INTERNSHIP CORE

### Backend

- Project
- ProjectTemplate
- Backlog
- Sprint
- Task
- Assignment

### Frontend

- Internship dashboard
- Project
- Sprint
- Kanban
- Task details

### Mentor

- Team management
- Task management
- Sprint management

### QA

- Permissions
- Dates
- Assignment
- Team isolation

### Acceptance

Student can execute:

```text
Project
 → Sprint
 → Task
 → Assignment
```

---

# 82. SPRINT 7 — SUBMISSION / REVIEW / EVALUATION

### Backend

- Submission
- Review
- Feedback
- Task completion
- Sprint evaluation
- Internship evaluation

### Frontend

- Submit
- Review
- Feedback
- Evaluation

### Mentor

- Review
- Feedback
- Scoring

### QA

```text
Submit
 → Review
 → Reject/Approve
 → Feedback
 → Complete
```

---

# 83. SPRINT 8 — LEARNING

### Backend

- Course
- Section
- Lesson
- Progress
- Quiz
- QuizAttempt
- Completion
- Skill relationships

### Frontend

- Catalog
- Course details
- Player
- Progress
- Quiz
- Completion

### QA

- Access
- Progress
- Quiz
- Completion

### Acceptance

```text
Course
 → Lesson
 → Progress
 → Quiz
 → Completion
```

---

# 84. SPRINT 9 — MENTORING / COMMUNICATION

### Backend

- Mentor
- Availability
- Booking
- Session
- Mentoring credits
- Chat
- Messages
- Notifications

### Frontend

- Mentor catalog
- Availability
- Booking
- Session
- Team chat
- Direct chat
- Notifications

### Realtime

- SignalR

### QA

- Booking conflicts
- Permissions
- Realtime
- Persistence
- Notifications

### Questions

- Session pricing؟
- Credits؟
- Cancellation؟
- Recording؟
- Standalone purchase؟

---

# 85. SPRINT 10 — ADMIN CORE

Admin:

- Students
- Mentors
- Tracks
- Skills
- Packages
- Courses
- Projects
- Teams
- Assessments
- Payments
- Enrollments
- Overrides
- Audit logs

### Acceptance

Admin can safely operate the platform without direct DB edits.

---

# 86. SPRINT 11 — ANALYTICS / PERFORMANCE / SECURITY

### Data

- Event validation
- KPI definitions
- Dashboards

### Backend

- Index review
- Query optimization
- Pagination audit
- Background jobs
- Rate limiting
- Authorization audit
- Security hardening

### QA

- Regression
- Integration
- E2E
- Load
- Stress
- Security

### DevOps

- Monitoring
- Alerts
- Backup
- Recovery testing

---

# 87. SPRINT 12 — MVP RELEASE

No major new features.

Focus:

- Bug fixing
- Security
- Performance
- Reliability
- Production config
- Monitoring
- Backups
- UAT
- Documentation
- Deployment
- Rollback

### Release Gate

All critical E2E flows pass.

---

# 88. DEPENDENCY MATRIX

| Module | Depends On |
|---|---|
| Profile | Identity |
| CV | Identity + Profile + Files |
| Tracks | Skills |
| Packages | Tracks + Entitlements |
| Checkout | Products + Packages |
| Payment | Checkout |
| Enrollment | Payment + Package |
| Assessment | Enrollment + Track |
| Team | Assessment + Track |
| Internship | Team + Project |
| Learning | Enrollment + Course |
| Mentoring | Enrollment/Standalone Product |
| Messaging | Identity + Team/Mentor |
| Notifications | Events |
| Certificate | Completion/Evaluation |
| Employer Recommendation | Evaluation + Profile + Internship |
| Analytics | All major modules |

---

# 89. DEFINITION OF READY

A feature is Ready when:

- Business rule is clear
- Acceptance criteria written
- UX available
- API contract defined
- Dependencies known
- Edge cases identified
- Security requirements identified
- QA scenarios identified

---

# 90. DEFINITION OF DONE

Feature is Done when:

- Code implemented
- Code reviewed
- Unit tests
- Integration tests where required
- API tests where required
- Frontend integrated
- Error states handled
- Authorization tested
- Logging added
- Audit added where needed
- Documentation updated
- No critical bugs
- Acceptance criteria passed

---

# 91. MVP CORE ACCEPTANCE CRITERIA

## Student

Can:

- Register
- Login
- Complete profile
- Upload CV when required
- Continue as beginner when allowed
- Select Track
- Select Package
- Pay
- Receive Enrollment
- Complete Assessment
- Receive Level
- Join Team
- Execute Internship
- Learn Courses
- Book Mentoring
- Chat
- Receive Notifications
- Complete Internship
- Receive Certificate according to final policy

---

# 92. PACKAGE LIFECYCLE ACCEPTANCE

The system must correctly handle:

```text
Purchase
Activation
Preparation
Internship
Completion
Expiry
Renewal
Upgrade
Cancellation
Refund
Pause
```

Every transition must be explicit and auditable.

---

# 93. PURCHASE ACCEPTANCE

For every purchase:

```text
Order Created
 ↓
Payment
 ↓
Provider Verification
 ↓
Webhook
 ↓
Idempotent Processing
 ↓
Entitlement/Enrollment Activation
```

No duplicate activation.

---

# 94. RENEWAL ACCEPTANCE

When Renewal is approved:

- Payment is verified
- Renewal relationship is recorded
- Previous history remains intact
- Entitlements are calculated correctly
- Dates are correct
- Track behavior follows policy
- No duplicate enrollment/access
- Audit record exists

---

# 95. UPGRADE ACCEPTANCE

When Upgrade is approved:

- Existing progress is preserved where applicable
- Price difference is calculated according to policy
- Payment is verified
- New entitlements activate correctly
- Team/Internship transition follows policy
- Audit record exists

---

# 96. STANDALONE SESSION ACCEPTANCE

Student can:

```text
Browse Session
 ↓
Purchase
 ↓
Receive Credit / Booking entitlement
 ↓
Choose Slot
 ↓
Book
 ↓
Receive Confirmation
 ↓
Attend
 ↓
Complete
 ↓
Feedback
```

Cancellation/refund/no-show behavior must follow the final policy.

---

# 97. FINAL MEETING DECISION LIST

The meeting should finish with explicit answers for:

### Business

1. 3-month beginner eligibility?
2. 6-month preparation duration?
3. 12-month internship timing?
4. Package prices?
5. Fixed package pricing or Track + Package?
6. Mentoring included or credits?
7. AI Mentor MVP or Phase 2?
8. Certificate trigger?
9. Employer recommendation MVP or Phase 2?
10. Refund policy?
11. Pause policy?
12. Renewal policy?
13. Upgrade policy?
14. Downgrade policy?
15. Standalone Session policy?

### Product

16. MVP Tracks?
17. Track change rules?
18. Level taxonomy?
19. Assessment attempts?
20. Retake policy?
21. Team size?
22. Mentor assignment?
23. Project template model?
24. Internship evaluation formula?
25. Learning prerequisites?

### Payment

26. Gateway?
27. Currency?
28. Tax/Invoice?
29. Promo codes?
30. Refunds?
31. Partial refunds?
32. Payment retry?
33. Order expiration?

### Technical

34. Object Storage?
35. Realtime scaling strategy?
36. Cache strategy?
37. Queue/background infrastructure?
38. Observability stack?
39. Backup strategy?
40. RPO/RTO?
41. Expected concurrent users?
42. Production deployment model?

### Privacy/Security

43. CV visibility?
44. AI data access?
45. Employer data sharing consent?
46. Data retention?
47. Account deletion?
48. File security?
49. Audit requirements?

---

# 98. DECISION LOG

| ID | Decision | Option A | Option B | Recommendation | Final Decision | Owner | Status |
|---|---|---|---|---|---|---|---|
| D-01 | 3M Beginner | Restricted | Allowed | TBD |  | Product | OPEN |
| D-02 | 6M Preparation | Fixed Gate | Dynamic Readiness | TBD |  | Product | OPEN |
| D-03 | 12M Internship | Fixed Date/Gate | Dynamic | TBD |  | Product | OPEN |
| D-04 | AI Mentor | MVP | Phase 2 | Phase 2 |  | Product/AI | OPEN |
| D-05 | Certificate | Package | Internship | Internship |  | Product | OPEN |
| D-06 | Mentoring | Unlimited | Credits | Credits |  | Product | OPEN |
| D-07 | Pricing | Fixed Package | Track + Package | Track + Package if needed |  | Product | OPEN |
| D-08 | Project | Admin | Template-driven | Template-driven + override |  | Product/Backend | OPEN |
| D-09 | Mentor | One Primary | Multiple | Support multiple, one primary initially |  | Operations | OPEN |
| D-10 | Duration Start | Payment | Journey Start | TBD |  | Product | OPEN |
| D-11 | Pause | No | Yes | TBD |  | Product | OPEN |
| D-12 | Refund | Strict | Flexible | TBD |  | Product/Finance | OPEN |
| D-13 | Employer Recommendation | MVP | Phase 2 | Phase 2 unless business requires |  | Product | OPEN |
| D-14 | Payment Gateway | Gateway A | Gateway B | TBD |  | Finance/Backend | OPEN |
| D-15 | MVP Tracks | TBD | TBD |  |  | Product | OPEN |
| D-16 | Level Model | Fixed | Configurable | Configurable |  | Product/AI | OPEN |
| D-17 | Renewal | New Enrollment | Extension | New Enrollment |  | Backend/Product | OPEN |
| D-18 | Upgrade | Supported | Phase 2 | Supported |  | Product/Backend | OPEN |
| D-19 | Downgrade | Supported | Phase 2 | Phase 2 |  | Product/Backend | OPEN |
| D-20 | Standalone Mentoring | Enrolled Only | Any User | TBD |  | Product | OPEN |

---

# 99. PHASE 2 CANDIDATES

Potentially defer:

- Full AI Mentor
- Employer Portal
- B2B University Portal
- B2B Company Portal
- Standalone Courses
- Advanced Career Marketplace
- Push Notifications
- Advanced Recommendation Engine
- Advanced Team Optimization
- Automated Employer Matching
- Subscription Billing
- Installments
- Advanced Gamification
- Advanced Social Features

---

# 100. IMPORTANT ARCHITECTURAL PRINCIPLES

## Principle 1 — Business Rules First

Do not encode unresolved business rules directly into code.

---

## Principle 2 — Package ≠ Track

Keep them independent.

---

## Principle 3 — Product ≠ Enrollment

A Package is what is sold.

Enrollment is the student's actual journey.

---

## Principle 4 — Payment ≠ Activation

Provider confirmation must be verified server-side.

---

## Principle 5 — AI ≠ Business Authority

AI recommends.

Backend decides.

Admin can override.

---

## Principle 6 — History Must Survive

Renewal, upgrade and new purchases must not destroy historical data.

---

## Principle 7 — Entitlements Over Hardcoded Package Logic

Prefer:

```text
Package
 → Entitlements
 → Policies
```

instead of:

```text
if package == 3
else if package == 6
else if package == 12
```

---

## Principle 8 — Files Outside SQL

SQL stores metadata.

Object Storage stores files.

---

## Principle 9 — Scale by Design, Not by Hype

Start with Modular Monolith.

Design clear boundaries.

Extract services only when real load/ownership/deployment needs justify it.

---

## Principle 10 — QA Starts Early

Testing is part of implementation, not post-implementation cleanup.

---

# 101. FINAL MVP FLOW

## Standard Student

```text
Visitor
 ↓
Register
 ↓
Profile
 ↓
CV
 ↓
Track
 ↓
Package
 ↓
Checkout
 ↓
Payment
 ↓
Enrollment
 ↓
AI Interview
 ↓
Level
 ↓
Team
 ↓
Project
 ↓
Sprints
 ↓
Tasks
 ↓
Submission
 ↓
Review
 ↓
Feedback
 ↓
Evaluation
 ↓
Certificate / Career Readiness
```

---

# 102. BEGINNER STUDENT

```text
Visitor
 ↓
Register
 ↓
Beginner Profile
 ↓
Track
 ↓
Package
 ↓
Payment
 ↓
Enrollment
 ↓
Foundation Learning
 ↓
Assessment
 ↓
Mentoring
 ↓
Projects
 ↓
Internship
 ↓
Evaluation
```

---

# 103. RENEWAL FLOW

```text
Existing Student
 ↓
Renew Package
 ↓
Eligibility Check
 ↓
Create Order
 ↓
Payment
 ↓
Verification
 ↓
New Enrollment / Extension
 ↓
Entitlements
 ↓
Continue Journey
```

---

# 104. UPGRADE FLOW

```text
Active Enrollment
 ↓
Upgrade Request
 ↓
Eligibility
 ↓
Calculate Difference
 ↓
Order
 ↓
Payment
 ↓
Verification
 ↓
Transition
 ↓
New Entitlements
 ↓
Continue
```

---

# 105. STANDALONE MENTORING FLOW

```text
Student
 ↓
Mentoring Session
 ↓
Choose Session Type
 ↓
Purchase
 ↓
Payment
 ↓
Credit
 ↓
Choose Mentor/Slot
 ↓
Booking
 ↓
Session
 ↓
Feedback
```

---

# 106. MVP SIGN-OFF

Before development is considered fully locked, the team must confirm:

- [ ] Business model
- [ ] Packages
- [ ] Package entitlements
- [ ] Pricing
- [ ] Renewal
- [ ] Upgrade
- [ ] Downgrade
- [ ] Standalone mentoring
- [ ] Refund
- [ ] Pause
- [ ] Track rules
- [ ] Assessment rules
- [ ] Level system
- [ ] Team rules
- [ ] Internship rules
- [ ] Learning rules
- [ ] Mentoring rules
- [ ] Certificate rules
- [ ] Employer recommendation scope
- [ ] MVP tracks
- [ ] Payment gateway
- [ ] Storage
- [ ] AI provider/strategy
- [ ] Security/privacy rules
- [ ] Analytics KPIs
- [ ] Scale targets
- [ ] RPO/RTO
- [ ] QA release gates

---

# 107. FINAL IMPLEMENTATION PHILOSOPHY

The MVP is not:

> "Build some screens and connect APIs."

The MVP is:

```text
Business Rules
      ↓
Domain Model
      ↓
Application Use Cases
      ↓
Infrastructure
      ↓
APIs
      ↓
Frontend
      ↓
AI / Payments / Files / Realtime
      ↓
Testing
      ↓
Observability
      ↓
Production
```

And every major business action must have:

```text
Command
 ↓
Validation
 ↓
Business Rules
 ↓
Transaction
 ↓
State Transition
 ↓
Audit/Event
 ↓
Notification/Background Work
```

The system must be designed so that adding a new Package, Track, Mentoring Product, AI provider, Payment provider, or future B2B capability does not require rewriting the Core.

**The goal of MVP is not maximum features.**

The goal is a **complete, reliable, scalable Core Journey**:

> **Discover → Buy → Enroll → Assess → Learn → Join Team → Execute Internship → Get Mentored → Get Evaluated → Become Career Ready.**


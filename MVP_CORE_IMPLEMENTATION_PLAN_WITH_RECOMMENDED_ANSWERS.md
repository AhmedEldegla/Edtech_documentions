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
  - **Recommended Answer:** [RECOMMENDED] نعم، Email verification مطلوبة قبل تفعيل الحساب المدفوع/الوصول الحساس. يمكن السماح بالتصفح قبلها. هذا يقلل الحسابات الوهمية بدون وضع احتكاك مبكر.
- هل Phone verification؟
  - **Recommended Answer:** [RECOMMENDED] ليست شرطاً للتسجيل في MVP. نطلبها فقط عند الحاجة الأمنية/الدفع/استرجاع الحساب، ويمكن جعلها اختيارية في البداية.
- هل social login في MVP؟
  - **Recommended Answer:** [RECOMMENDED] لا في Core MVP. Email/password أولاً؛ Social Login Phase 2 لتقليل scope ومشاكل الهوية والربط.
- هل user يستطيع تغيير email؟
  - **Recommended Answer:** [RECOMMENDED] نعم مع إعادة verification للعنوان الجديد، وإلغاء الجلسات الحساسة عند التغيير.
- هل user يستطيع حذف account؟
  - **Recommended Answer:** [RECOMMENDED] نعم، مع soft-delete للحساب وحفظ السجلات المالية والتدقيق التي يلزم الاحتفاظ بها قانونياً/تشغيلياً.
- ما required profile fields؟
  - **Recommended Answer:** [RECOMMENDED] الاسم، الدولة/المدينة، التعليم، المهارات الأساسية، الخبرة إن وجدت، الهدف المهني، Track المفضل، availability. لا نطلب بيانات لا تؤثر على الخدمة.
- هل profile completion شرط للدفع؟
  - **Recommended Answer:** [RECOMMENDED] لا. اسمح بالشراء بعد الحد الأدنى من بيانات الهوية، ثم اجعل الحقول اللازمة للـEnrollment شرطاً قبل التفعيل. الهدف تقليل drop-off عند checkout.
- أم شرط للـenrollment activation؟
  - **Recommended Answer:** [RECOMMENDED] نعم، الحد الأدنى المطلوب للتشغيل يجب اكتماله قبل تفعيل الـEnrollment فعلياً.
- هل profile changes بعد assessment تؤثر على assessment؟
  - **Recommended Answer:** [RECOMMENDED] لا تغيّر نتيجة Assessment تاريخياً. أي بيانات جديدة تؤثر على تقييم لاحق فقط؛ نخزن snapshot للبيانات المستخدمة.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل profile data versioned؟
  - **Recommended Answer:** [RECOMMENDED] نعم على مستوى snapshots المهمة، وليس كل field-change بشكل مبالغ فيه. نحتاج traceability بدون تضخيم البيانات.

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
  - **Recommended Answer:** [RECOMMENDED] نعم بلا قيود.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- بعد الدفع؟
  - **Recommended Answer:** [RECOMMENDED] نعم قبل بدء Assessment/Internship مع تحديث الـEnrollment/entitlements بطريقة واضحة. بعد بدء المسار تصبح Track change controlled.
- بعد assessment؟
  - **Recommended Answer:** [RECOMMENDED] مسموحة قبل Team Assignment فقط، ويفضل إعادة تقييم إذا كانت Track مختلفة جذرياً.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- بعد team assignment؟
  - **Recommended Answer:** [RECOMMENDED] لا كـself-service. تتم بطلب ومراجعة Admin لأن تغيير Track هنا قد يكسر team/project capacity.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- بعد internship؟
  - **Recommended Answer:** [RECOMMENDED] لا تغيّر تاريخ الـTrack السابقة. يمكن شراء/بدء Enrollment جديدة في Track أخرى.
- هل changing track يلغي assessment؟
  - **Recommended Answer:** [RECOMMENDED] إذا كانت Track مختلفة في competency model، نعتبر الـassessment القديم غير صالح للمسار الجديد ونطلب assessment مناسباً.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل يلغي project؟
  - **Recommended Answer:** [RECOMMENDED] لا نحذف المشروع القديم. إذا حدث انتقال معتمد قبل التنفيذ، يتم إغلاق assignment القديمة وتسجيل transition ثم إنشاء assignment جديدة عند الحاجة.
- هل course progress يتأثر؟
  - **Recommended Answer:** [RECOMMENDED] لا يُحذف progress. نحتفظ بالتاريخ ونحدد access الجديد حسب package/track.
- هل يحتاج Admin approval؟
  - **Recommended Answer:** [RECOMMENDED] فقط بعد نقاط الخطر: assessment/team/internship start. قبل ذلك self-service.
- هل student يستطيع شراء enrollments في Tracks مختلفة؟
  - **Recommended Answer:** [RECOMMENDED] نعم، لكن لا نسمح بتشغيل مسارين Internship متعارضين في الوقت نفسه. يمكن امتلاك تاريخ/Access متعدد مع business rules واضحة.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.

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
  - **Recommended Answer:** [RECOMMENDED] Attempt أساسي واحد لكل enrollment + Retake واحد عند الحاجة. يمكن زيادة العدد مستقبلاً حسب البيانات، مع rate limits لمنع abuse.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل Retake مسموح؟
  - **Recommended Answer:** [RECOMMENDED] نعم عند failure أو technical issue، لكن ليس بلا حدود.
- هل الـRetake overwrites result أم version جديدة؟
  - **Recommended Answer:** [RECOMMENDED] Version جديدة دائماً؛ النتيجة القديمة immutable وتبقى audit history.
- هل student يستطيع Resume؟
  - **Recommended Answer:** [RECOMMENDED] نعم إذا كان الـAssessment مصمم كجلسة قابلة للاستئناف؛ otherwise نستخدم checkpoints. لا نضيع محاولة بسبب إغلاق المتصفح.
- ماذا يحدث عند disconnect؟
  - **Recommended Answer:** [RECOMMENDED] نحفظ progress/checkpoint، ونستأنف ضمن نافذة زمنية. لا تُحتسب محاولة فاشلة بسبب عطل تقني مثبت.
- هل يوجد time limit؟
  - **Recommended Answer:** [RECOMMENDED] نعم، limit مناسب لكل assessment، مع grace period بسيط للاتصال. الهدف قياس competency وليس سرعة الإنترنت.
- هل questions randomized؟
  - **Recommended Answer:** [RECOMMENDED] نعم من question bank مع blueprint ثابت حتى تظل صعوبة الاختبارات متقاربة.
- هل AI generates questions أم question bank؟
  - **Recommended Answer:** [RECOMMENDED] Core MVP يعتمد question bank منظم؛ AI يمكنه التوليد/التكييف داخل حدود template لاحقاً. لا نعتمد على generation الحر وحده في قرار تجاري.
- هل AI-generated questions تحتاج review؟
  - **Recommended Answer:** [RECOMMENDED] نعم، خاصة أي سؤال يدخل في scoring. AI-generated content يجب validation/review قبل اعتماده كعنصر scored.
- ماذا يحدث إذا AI provider down؟
  - **Recommended Answer:** [RECOMMENDED] نستخدم fallback إلى rule/question-bank assessment. الـbusiness flow لا يتوقف بالكامل بسبب مزود AI.
- هل يوجد fallback rules؟
  - **Recommended Answer:** [RECOMMENDED] نعم. الـbackend هو صاحب القرار النهائي، وAI خدمة مساعدة وليست single point of failure.
- هل يوجد human review؟
  - **Recommended Answer:** [RECOMMENDED] نعم للحالات borderline، appeals، وAI confidence المنخفض.
- هل AI score يمكن تغييره بواسطة Admin؟
  - **Recommended Answer:** [RECOMMENDED] نعم لكن كـoverride منفصل، مع السبب والفاعل والوقت، ولا نعدل الـraw AI result.
- هل result لها expiration؟
  - **Recommended Answer:** [RECOMMENDED] نعم بشكل عملي 6–12 شهراً أو عند تغيير Track competency materially. نستخدم policy قابلة للتهيئة.
- هل Renewal يحتاج assessment؟
  - **Recommended Answer:** [RECOMMENDED] لا إذا كانت نفس Track والنتيجة ما زالت صالحة. نعيد assessment فقط عند انتهاء صلاحيتها أو تغيير المسار/المستوى المطلوب.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل Upgrade يحتاج assessment؟
  - **Recommended Answer:** [RECOMMENDED] لا افتراضياً؛ يعاد فقط إذا كان upgrade يغيّر Track/competency gate بشكل جوهري.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- كيف نضمن consistency؟
  - **Recommended Answer:** [RECOMMENDED] versioned rubrics + question blueprints + deterministic backend rules + model/prompt versioning + calibration/review.
- هل نخزن model/prompt version؟
  - **Recommended Answer:** [RECOMMENDED] نعم لكل AI decision مؤثر في business flow.

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
  - **Recommended Answer:** [RECOMMENDED] 3 مستويات بسيطة في MVP: Beginner / Intermediate / Advanced، ويمكن توسيعها لاحقاً.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل كل Track لها levels مختلفة؟
  - **Recommended Answer:** [RECOMMENDED] taxonomy موحدة قدر الإمكان، مع competency criteria مختلفة لكل Track.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- ما scoring formula؟
  - **Recommended Answer:** [RECOMMENDED] نبدأ بوزن واضح وقابل للتفسير: technical/skill competency هو الأعلى، ثم problem solving، ثم communication/behavioral. التفاصيل تُضبط لكل Track عبر rubric.
- هل score ثابت؟
  - **Recommended Answer:** [RECOMMENDED] thresholds ثابتة لكل version من rubric، لكن rubric نفسها versioned ويمكن تحديثها للأجيال الجديدة دون تغيير النتائج القديمة.
- هل skill gaps لها وزن؟
  - **Recommended Answer:** [RECOMMENDED] نعم، كعامل readiness/recommendation أكثر من كونها عقوبة. Missing skills تحدد preparation path ولا تمنع الطالب تلقائياً إلا عند core prerequisites.
- هل AI recommendation يمكنها تغيير level؟
  - **Recommended Answer:** [RECOMMENDED] لا مباشرة. AI يقدم recommendation + confidence، والbackend rules تحدد level النهائي.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل Admin يستطيع override؟
  - **Recommended Answer:** [RECOMMENDED] نعم مع reason.
- هل override يحتاج reason؟
  - **Recommended Answer:** [RECOMMENDED] نعم إلزامي.
- هل override يدخل في audit log؟
  - **Recommended Answer:** [RECOMMENDED] نعم إلزامي.

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
  - **Recommended Answer:** [RECOMMENDED] نعم لكل purchase/enrollmentable product وفق policy، مع idempotency لمنع التكرار.
- هل الطالب يستطيع امتلاك أكثر من Active Enrollment؟
  - **Recommended Answer:** [RECOMMENDED] نعم إذا كانت لمسارات/منتجات غير متعارضة، لكن لا نسمح بتضارب internship schedules.
- هل two enrollments لنفس Track مسموحة؟
  - **Recommended Answer:** [RECOMMENDED] لا افتراضياً. استخدم Renewal/Upgrade بدلاً من duplication.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل enrollments يمكن أن تعمل concurrently؟
  - **Recommended Answer:** [RECOMMENDED] فقط إذا لم تتعارض في internship/team/mentor resources؛ learning-only enrollments يمكن أن تتزامن.
- هل enrollment جديدة توقف القديمة؟
  - **Recommended Answer:** [RECOMMENDED] لا تلقائياً. الـtransition يحدد إن كانت renewal/upgrade continuation أو مساراً مستقلاً.
- هل student يحتفظ بالـprevious package access؟
  - **Recommended Answer:** [RECOMMENDED] التاريخ محفوظ، لكن access التشغيلي ينتهي بانتهاء entitlement.
- ماذا يحدث عند expiry أثناء Internship؟
  - **Recommended Answer:** [RECOMMENDED] لا نقطع internship الجاري فجأة. نعطي grace/continuation policy محددة، ثم يتوقف access إذا لم يوجد تجديد أو حالة استثناء.
- هل team/chat تستمر بعد expiry؟
  - **Recommended Answer:** [RECOMMENDED] Team workspace والرسائل الأساسية تبقى للقراءة لفترة retention، لكن actions الحية تتوقف عند انتهاء access إلا إذا policy تسمح.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل admin يستطيع Reactivate؟
  - **Recommended Answer:** [RECOMMENDED] نعم بصلاحية محددة وسبب mandatory، وليس كتصرف عادي.
- هل Enrollment قابلة للتحويل لمستخدم آخر؟
  - **Recommended Answer:** [RECOMMENDED] لا. الـenrollment شخصية وغير قابلة للبيع/النقل لحماية النزاهة ومنع fraud.
- هل Pause مسموح؟
  - **Recommended Answer:** [RECOMMENDED] نعم مرة/مرتين حسب package، للحالات المبررة أو business policy، وليس unlimited.
- هل Progress يتجمد؟
  - **Recommended Answer:** [RECOMMENDED] نعم. لا نخسر progress ولا نسمح بتغييرات أكاديمية غير مقصودة أثناء pause.
- هل Mentor/Team assignment تتجمد؟
  - **Recommended Answer:** [RECOMMENDED] نعم assignment محفوظ، مع إعادة توزيع فقط إذا أثرت المدة على capacity.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.

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
  - **Recommended Answer:** [RECOMMENDED] نعم كـUpgrade واضح، ويفضل قبل أو في بداية internship لتقليل operational complexity.
- هل 6M → 12M؟
  - **Recommended Answer:** [RECOMMENDED] نعم كـUpgrade، مع preservation للـprogress.
- هل 12M → 6M؟
  - **Recommended Answer:** [RECOMMENDED] لا كـdowngrade أثناء دورة نشطة في MVP؛ نسمح بإكمال current entitlement أو الاستفادة من policy renewal لاحقاً.
- هل downgrade مسموح؟
  - **Recommended Answer:** [RECOMMENDED] Phase 2. الـMVP يدعم upgrade/renewal فقط لتقليل refund/accounting complexity.
- هل upgrade فقط قبل Internship؟
  - **Recommended Answer:** [RECOMMENDED] الأفضل أن يكون مسموحاً قبل internship أو في نافذة مبكرة محددة. بعد دخول مشروع متقدم يحتاج review لأن resources قد تتغير.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل upgrade بعد Internship يبدأ؟
  - **Recommended Answer:** [RECOMMENDED] يمكن أن يمدد career/learning access، لكن لا يعيد internship من الصفر.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- كيف نحسب price difference؟
  - **Recommended Answer:** [RECOMMENDED] Upgrade price = target package price − value of unused eligible entitlement، مع قواعد واضحة تمنع arbitrage.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل نستخدم unused time credit؟
  - **Recommended Answer:** [RECOMMENDED] نعم بشكل محدود على قيمة access غير المستخدمة، وليس refund نقدي مفتوح.
- هل upgrade فوري؟
  - **Recommended Answer:** [RECOMMENDED] بعد payment verification فقط. الـentitlement transition transactionally.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل يحتاج reassessment؟
  - **Recommended Answer:** [RECOMMENDED] لا إلا إذا كان upgrade يتطلب competency gate جديداً.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل Team تتغير؟
  - **Recommended Answer:** [RECOMMENDED] لا افتراضياً؛ نغيّرها فقط إذا تغير المستوى/Track/المشروع.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل Project يتغير؟
  - **Recommended Answer:** [RECOMMENDED] لا افتراضياً.
- هل progress يظل؟
  - **Recommended Answer:** [RECOMMENDED] نعم بالكامل حيثما كان المحتوى مشتركاً.
- هل certificate يتأثر؟
  - **Recommended Answer:** [RECOMMENDED] الشهادة تمثل achievement الفعلي؛ upgrade لا يمس الشهادة القديمة، ويمكن إصدار credential جديد عند استيفاء achievement جديد.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل Track يمكن تغييرها مع upgrade؟
  - **Recommended Answer:** [RECOMMENDED] لا كعملية واحدة في MVP. Track change وUpgrade عمليتان منفصلتان لتجنب حالات محاسبية معقدة.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- ماذا يحدث إذا upgrade payment failed؟
  - **Recommended Answer:** [RECOMMENDED] يُحسم بنفس business rule الموجودة في القسم الرئيسي، ويجب تسجيل القرار في Decision Log قبل التنفيذ.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- ماذا يحدث إذا payment succeeded but activation failed؟
  - **Recommended Answer:** [RECOMMENDED] يُحسم بنفس business rule الموجودة في القسم الرئيسي، ويجب تسجيل القرار في Decision Log قبل التنفيذ.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل توجد upgrade discount rules؟
  - **Recommended Answer:** [RECOMMENDED] نعم policy بسيطة وشفافة، لا discounts يدوية غير قابلة للتدقيق.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.

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
  - **Recommended Answer:** [RECOMMENDED] نعم حتى غير enrolled، لأن standalone mentoring قناة revenue مستقلة.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل لازم يكون enrolled؟
  - **Recommended Answer:** [RECOMMENDED] لا للـstandalone؛ الـpackage mentoring مرتبط بالـenrollment.
- هل active students يستطيعون شراء extra sessions؟
  - **Recommended Answer:** [RECOMMENDED] نعم.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل session مرتبطة بـTrack؟
  - **Recommended Answer:** [RECOMMENDED] يفضل ربطها بTrack/skill context اختيارياً، وليس إلزامياً لكل session.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل session مرتبطة بـMentor؟
  - **Recommended Answer:** [RECOMMENDED] نعم عند الحجز النهائي.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل student يختار mentor؟
  - **Recommended Answer:** [RECOMMENDED] نعم إذا كان mentor متاحاً، مع auto-assignment كـfallback.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل mentor يحدد سعره؟
  - **Recommended Answer:** [RECOMMENDED] لا في MVP؛ pricing مركزي للحفاظ على تجربة موحدة وهامش ربح متوقع.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل السعر حسب duration؟
  - **Recommended Answer:** [RECOMMENDED] نعم، duration tiers واضحة.
- هل duration 30/45/60 minutes؟
  - **Recommended Answer:** [RECOMMENDED] 30 و60 دقيقة في MVP؛ 45 دقيقة يمكن إضافتها لاحقاً إذا ظهر طلب.
- هل credits expiry؟
  - **Recommended Answer:** [RECOMMENDED] نعم expiry واضحة، مثلاً 90 يوماً، لحماية revenue recognition وتشجيع الاستخدام.
- هل unused credit rollover؟
  - **Recommended Answer:** [RECOMMENDED] لا افتراضياً، إلا إذا كان credit جزءاً من renewal أو policy خاصة.
- هل Session قابلة للنقل؟
  - **Recommended Answer:** [RECOMMENDED] لا بين users. يمكن إعادة الجدولة لنفس المستخدم.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل Session لها refund؟
  - **Recommended Answer:** [RECOMMENDED] نعم قبل نافذة الإلغاء؛ بعد انعقاد الجلسة لا refund إلا في mentor/provider failure.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- Cancellation policy؟
  - **Recommended Answer:** [RECOMMENDED] إلغاء مجاني قبل 24 ساعة، وبعدها credit يعود جزئياً/لا يعود حسب المنتج. سياسة واحدة واضحة.
- Reschedule policy؟
  - **Recommended Answer:** [RECOMMENDED] مرة واحدة مجاناً قبل 24 ساعة؛ mentor no-show يعيد credit كاملاً.
- Student no-show؟
  - **Recommended Answer:** [RECOMMENDED] بعد grace period تعتبر consumed، مع exception محدود.
- Mentor no-show؟
  - **Recommended Answer:** [RECOMMENDED] credit كامل + priority reschedule، مع tracking لجودة mentor.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل booking confirmation تعمل Order؟
  - **Recommended Answer:** [RECOMMENDED] الشراء يخلق Order؛ booking تستهلك entitlement/credit. لا ننشئ payment order جديداً لكل reschedule.
- هل Session لها meeting link؟
  - **Recommended Answer:** [RECOMMENDED] نعم، generated/protected link لا يظهر إلا للأطراف المصرح لهم.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل recording موجود؟
  - **Recommended Answer:** [RECOMMENDED] لا في Core MVP افتراضياً؛ يقلل privacy/storage complexity. يمكن تفعيله لاحقاً لبعض products.
- من يقدر يشوف recording؟
  - **Recommended Answer:** [RECOMMENDED] إذا أضيفت لاحقاً: الطالب + mentor فقط وبصلاحية signed URL.
- كم مدة الاحتفاظ بالتسجيل؟
  - **Recommended Answer:** [RECOMMENDED] إذا أضيف: retention قصيرة ومعلنة مثل 30–90 يوماً.
- هل توجد Session notes؟
  - **Recommended Answer:** [RECOMMENDED] نعم، notes مختصرة من mentor، مرتبطة بالجلسة ومحمية حسب role.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل يوجد rating؟
  - **Recommended Answer:** [RECOMMENDED] نعم بعد الجلسة، rating + optional feedback، وتدخل في mentor quality metrics.
- هل session تدخل في student's career history؟
  - **Recommended Answer:** [RECOMMENDED] نعم كـcompleted mentoring activity، بدون تضخيمها كخبرة عمل.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.

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
  - **Recommended Answer:** [RECOMMENDED] نختار gateway يدعم البطاقات وطرق الدفع المحلية مثل wallets/Fawry حسب availability والتكلفة. القرار النهائي بعد مقارنة fees, settlement, webhooks, refunds, support.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- Currency؟
  - **Recommended Answer:** [RECOMMENDED] EGP في السوق المصري أولاً، مع تصميم يدعم multi-currency لاحقاً.
- هل VAT/Tax موجود؟
  - **Recommended Answer:** [RECOMMENDED] نحسب الضرائب وفق الكيان القانوني واللوائح الحالية، ولا نضع نسبة ثابتة داخل domain. Tax configuration تكون قابلة للتغيير.
- هل Invoice مطلوب؟
  - **Recommended Answer:** [RECOMMENDED] نعم إيصال/فاتورة لكل transaction حسب المتطلبات القانونية والكيان الضريبي.
- هل Promo Codes؟
  - **Recommended Answer:** [RECOMMENDED] نعم لكن بسيستم بسيط: validity, usage limit, package/track scope, max discount, audit.
- هل Discounts؟
  - **Recommended Answer:** [RECOMMENDED] نعم عبر rules/promo campaigns وليس price mutation يدوي.
- هل Installments؟
  - **Recommended Answer:** [RECOMMENDED] لا في Core MVP إلا إذا gateway/business validation أثبتت أنها ضرورية. أضفها بعد فهم default cash conversion.
- ماذا لو payment succeeds والـwebhook متأخر؟
  - **Recommended Answer:** [RECOMMENDED] Order تبقى Pending/Processing، ونقوم بالتحقق server-to-server عند الحاجة؛ لا نعتمد على client callback.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- ماذا لو webhook duplicate؟
  - **Recommended Answer:** [RECOMMENDED] idempotent processing باستخدام provider transaction ID + internal idempotency key.
- ماذا لو client says success والbackend لم يؤكد؟
  - **Recommended Answer:** [RECOMMENDED] نظهر Processing ونؤكد من provider/backend. لا نفعّل entitlement بناءً على client فقط.
- ماذا لو amount مختلف؟
  - **Recommended Answer:** [RECOMMENDED] نرفض activation ونضع payment في exception/reconciliation queue حتى يراجعها النظام/Finance.
- ماذا لو order expired؟
  - **Recommended Answer:** [RECOMMENDED] لا نقبل payment على order expired إلا إذا provider flow يعيدها بشكل آمن؛ الأفضل إنشاء Order جديد.
- هل retry payment على نفس Order؟
  - **Recommended Answer:** [RECOMMENDED] نعم طالما order ما زال صالحاً، مع منع concurrent attempts غير الضرورية.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل يمكن دفع نفس Order مرتين؟
  - **Recommended Answer:** [RECOMMENDED] technically يمكن أن تصل محاولتان، لكن النظام يمنع double activation ويحوّل الزائدة إلى reconciliation/refund flow.
- كيف نمنع duplicate activation؟
  - **Recommended Answer:** [RECOMMENDED] unique constraints + idempotent webhook handler + transaction boundary.
- Partial refund؟
  - **Recommended Answer:** [RECOMMENDED] نعم بناءً على entitlement usage وpolicy ثابتة.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- Full refund؟
  - **Recommended Answer:** [RECOMMENDED] نعم ضمن نافذة refund والسياسة.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- Chargeback؟
  - **Recommended Answer:** [RECOMMENDED] يسجل كـfinancial dispute ويوقف/يقيد access حسب risk policy، بدون حذف history.
- Reconciliation process؟
  - **Recommended Answer:** [RECOMMENDED] daily automated reconciliation + exception queue للمبالغ/transactions غير المتطابقة.
- من يملك financial permissions؟
  - **Recommended Answer:** [RECOMMENDED] Finance role منفصل عن super admin قدر الإمكان، مع least privilege وaudit.

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
  - **Recommended Answer:** [RECOMMENDED] نعم وفق refund policy، لكن الإلغاء لا يعني حذف الـhistory.
- خلال كم ساعة/يوم؟
  - **Recommended Answer:** [RECOMMENDED] نافذة واضحة مثل 7 أيام من الشراء، بشرط عدم استهلاك خدمات جوهرية؛ الرقم النهائي يراجع قانونياً وتجاريًا.
- هل بعد بدء Internship؟
  - **Recommended Answer:** [RECOMMENDED] refund كامل لا. فقط exceptional/partial refund وفق الاستهلاك والسياسة.
- هل بعد استخدام Course؟
  - **Recommended Answer:** [RECOMMENDED] إذا استُهلك جزء جوهري من المحتوى، يتحول إلى partial/credit policy بدلاً من full refund.
- هل بعد استخدام Session؟
  - **Recommended Answer:** [RECOMMENDED] الجلسة المكتملة تُعتبر consumed ولا تُرد، بينما credits غير المستخدمة تخضع للسياسة.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل بعد Assessment؟
  - **Recommended Answer:** [RECOMMENDED] assessment يستهلك service cost، لذلك refund بعده يكون partial/exceptional.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل refund كامل؟
  - **Recommended Answer:** [RECOMMENDED] فقط ضمن نافذة الإلغاء وقبل استهلاك الخدمات الأساسية.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- Partial refund؟
  - **Recommended Answer:** [RECOMMENDED] نعم بناءً على entitlement usage وpolicy ثابتة.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل transaction fees تُخصم؟
  - **Recommended Answer:** [RECOMMENDED] حسب gateway/legal terms؛ الأفضل عدم إظهارها كرسوم غامضة، بل تضمينها في policy واضحة قبل الدفع.
- ماذا يحدث للـEnrollment؟
  - **Recommended Answer:** [RECOMMENDED] تتحول إلى Cancelled/Refunded ولا تحذف.
- ماذا يحدث للـcertificate؟
  - **Recommended Answer:** [RECOMMENDED] إذا لم يستوفِ achievement يبقى غير صادر؛ إذا كانت شهادة صدرت ثم ثبت refund بعد completion، revoke وفق policy.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- ماذا يحدث للـteam؟
  - **Recommended Answer:** [RECOMMENDED] student يخرج من active team assignment، ولا نحذف team history.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- ماذا يحدث للـchat؟
  - **Recommended Answer:** [RECOMMENDED] history محفوظ وفق retention، access التشغيلي يتوقف حسب policy.
- ماذا يحدث للـfiles؟
  - **Recommended Answer:** [RECOMMENDED] لا نحذف فوراً إذا كانت مرتبطة بسجلات؛ نطبق retention/deletion policy.
- ماذا يحدث للـcredits؟
  - **Recommended Answer:** [RECOMMENDED] unused credits تُلغى/تعود حسب سبب refund؛ لا نسمح بالاستفادة منها بعد refund.

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
  - **Recommended Answer:** [RECOMMENDED] نعم بحدود واضحة.
- كم مرة؟
  - **Recommended Answer:** [RECOMMENDED] مرة افتراضياً.
- maximum duration؟
  - **Recommended Answer:** [RECOMMENDED] 14–30 يوماً حسب package.
- هل EndDate يتم تمديده؟
  - **Recommended Answer:** [RECOMMENDED] نعم بمقدار pause approved.
- هل Internship pauses؟
  - **Recommended Answer:** [RECOMMENDED] نعم إذا pause رسمية؛ sprint/task clocks تتوقف أو يعاد جدولتها وفق policy.
- هل Team تستمر؟
  - **Recommended Answer:** [RECOMMENDED] assignment محفوظة ما أمكن.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل Mentor تستمر؟
  - **Recommended Answer:** [RECOMMENDED] لا نضمن نفس mentor إذا امتدت pause؛ نحتفظ بالـassignment ونسمح بإعادة الجدولة.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل Tasks تتوقف؟
  - **Recommended Answer:** [RECOMMENDED] نعم أثناء pause الرسمية.
- هل Chat يتوقف؟
  - **Recommended Answer:** [RECOMMENDED] read access يمكن أن يستمر، لكن active collaboration notifications تتوقف حسب policy.
- هل credits تتوقف؟
  - **Recommended Answer:** [RECOMMENDED] نعم، expiration تمدد بقدر pause فقط إذا كانت credits جزءاً من نفس enrollment.
- هل Admin يستطيع force pause؟
  - **Recommended Answer:** [RECOMMENDED] نعم لحالات operational/exception، مع reason وaudit.
- هل medical/emergency/business reasons لها policies مختلفة؟
  - **Recommended Answer:** [RECOMMENDED] يمكن وجود exception policy واحدة للحالات الموثقة، بدون بناء عشرات الحالات في MVP.

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
  - **Recommended Answer:** [RECOMMENDED] لا نضع الطالب في team سيئة. نستخدم waitlist/temporary cohort أو mentor-led individual preparation حتى يكتمل الحد الأدنى.
- ماذا لو عدد الطلاب كبير؟
  - **Recommended Answer:** [RECOMMENDED] queue/cohort formation على دفعات، team capacity limits، ولا نفتح cohort أكثر من قدرة mentors/projects.
- هل team incomplete مسموحة؟
  - **Recommended Answer:** [RECOMMENDED] نعم فقط إذا الحد الأدنى التشغيلي متحقق؛ وإلا waitlist.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل team size ثابت أم configurable؟
  - **Recommended Answer:** [RECOMMENDED] configurable لكل project template مع default ثابت في MVP.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- ماذا لو Mentor unavailable؟
  - **Recommended Answer:** [RECOMMENDED] fallback mentor pool + capacity queue؛ لا نؤخر الطالب بلا نهاية.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل student يطلب team change؟
  - **Recommended Answer:** [RECOMMENDED] نعم request-based، لكن ليس self-service immediate.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل Admin يستطيع نقل student؟
  - **Recommended Answer:** [RECOMMENDED] نعم مع reason + audit + validation of capacity.
- ماذا يحدث للـtasks؟
  - **Recommended Answer:** [RECOMMENDED] تبقى history؛ يتم reassignment للمهام المفتوحة فقط وفق policy.
- ماذا يحدث للـperformance history؟
  - **Recommended Answer:** [RECOMMENDED] لا تنتقل بشكل يزوّر attribution؛ history مرتبطة بالstudent والteam/project context.
- هل team merge/split مسموح؟
  - **Recommended Answer:** [RECOMMENDED] Admin-only في MVP، ويُستخدم كاستثناء تشغيلي.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل team size يتغير أثناء project؟
  - **Recommended Answer:** [RECOMMENDED] نعم عند الضرورة، لكن project/team template يحدد الحدود.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- ماذا لو Skill مهمة غير موجودة؟
  - **Recommended Answer:** [RECOMMENDED] لا نخلق team matching وهمي. نستخدم skill gap + mentor support أو نعيد توزيع الطالب.
- هل AI recommendation قابلة للoverride؟
  - **Recommended Answer:** [RECOMMENDED] نعم، backend/business rules + Admin override.
- هل يجب إظهار سبب الـmatching؟
  - **Recommended Answer:** [RECOMMENDED] نعم بشكل مبسط: skills fit, level, availability, project needs. هذا يبني الثقة ويقلل اعتراضات الطلاب.

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
  - **Recommended Answer:** [RECOMMENDED] Mentor أساسي واحد في MVP، مع إمكانية supporting mentors تقنياً.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل Mentor متعدد؟
  - **Recommended Answer:** [RECOMMENDED] ليس كـdefault. نسمح supporting mentor عند الحاجة.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل mentor assignment تلقائي؟
  - **Recommended Answer:** [RECOMMENDED] يمكن AI/rules اقتراحه، لكن assignment النهائي يخضع للcapacity/business rules.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل admin assignment؟
  - **Recommended Answer:** [RECOMMENDED] نعم كfallback وoverride.
- هل mentor capacity لها limit؟
  - **Recommended Answer:** [RECOMMENDED] نعم، configurable، وهي constraint أساسي في team formation.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- ماذا يحدث عند mentor absence؟
  - **Recommended Answer:** [RECOMMENDED] reassignment أو backup mentor، مع SLA واضح.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل students يمكنهم طلب mentor؟
  - **Recommended Answer:** [RECOMMENDED] نعم للـstandalone أو support request؛ team mentor لا يضمن اختياراً شخصياً.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل mentor يرى كل student data؟
  - **Recommended Answer:** [RECOMMENDED] لا. least privilege؛ يرى ما يحتاجه للتوجيه والتقييم فقط.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل mentor يستطيع تغيير level؟
  - **Recommended Answer:** [RECOMMENDED] لا مباشرة. يقدم recommendation؛ Admin/backend يطبق القرار.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل mentor evaluation تؤثر على final score؟
  - **Recommended Answer:** [RECOMMENDED] نعم بوزن محدود، لأنها practical evidence، لكن لا تكون العامل الوحيد.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.

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
  - **Recommended Answer:** [RECOMMENDED] المصدر الأساسي Track/Project Template مع Admin management؛ لا نبني كل project من الصفر لكل team.
- أم Track template-driven؟
  - **Recommended Answer:** [RECOMMENDED] نعم، template-driven مع parameters/variants.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل team تستطيع اختيار project؟
  - **Recommended Answer:** [RECOMMENDED] اختيار محدود من المشاريع المناسبة لمستوى/Track، وليس free-for-all.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل project يتغير بعد البدء؟
  - **Recommended Answer:** [RECOMMENDED] فقط بقرار Admin/mentor لأسباب قوية؛ لا نسمح بتغيير يفرغ evaluation من معناها.
- ماذا يحدث إذا project cancelled؟
  - **Recommended Answer:** [RECOMMENDED] migrate team إلى approved template مع preservation of completed work/history.
- هل project reusable؟
  - **Recommended Answer:** [RECOMMENDED] نعم كـtemplate؛ كل execution له ProjectInstance مستقل.
- هل projects لها versions؟
  - **Recommended Answer:** [RECOMMENDED] نعم templates versioned حتى لا تتغير مشاريع الطلاب التاريخية.
- هل template لها owner؟
  - **Recommended Answer:** [RECOMMENDED] نعم owner/maintainer داخلي مع approval workflow.
- هل tasks تتولد تلقائياً؟
  - **Recommended Answer:** [RECOMMENDED] نعم من template عند إنشاء project/sprint، مع إمكانية تعديل mentor/admin.

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
  - **Recommended Answer:** [RECOMMENDED] نعم cohort-based default، مع extensions controlled.
- هل mentor يستطيع extend؟
  - **Recommended Answer:** [RECOMMENDED] يوصي/يطلب extension، لكن لا يمدد بشكل مفتوح دون rule.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل Admin يستطيع extend؟
  - **Recommended Answer:** [RECOMMENDED] نعم مع reason/audit.
- هل student يعمل ahead؟
  - **Recommended Answer:** [RECOMMENDED] نعم إذا dependencies تسمح، لكن لا يغيّر sprint deadlines الرسمية.
- ماذا يحدث عند missed sprint؟
  - **Recommended Answer:** [RECOMMENDED] ينعكس على performance، مع recovery plan بدلاً من عقوبة فورية.
- هل rejected task يرجع InProgress؟
  - **Recommended Answer:** [RECOMMENDED] نعم مع mandatory feedback.
- هل Done task يمكن reopen؟
  - **Recommended Answer:** [RECOMMENDED] نعم للmentor/admin فقط مع reason.
- هل due date قابلة للتغيير؟
  - **Recommended Answer:** [RECOMMENDED] نعم controlled، ولا نسمح بتعديل التاريخ لإخفاء التأخير.
- هل sprint score يدخل في final evaluation؟
  - **Recommended Answer:** [RECOMMENDED] نعم كجزء من delivery consistency، بوزن محدود.

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
  - **Recommended Answer:** [RECOMMENDED] mentor/admin من template، والstudent يستطيع create personal subtask إذا احتجناها لاحقاً.
- هل student يستطيع create task؟
  - **Recommended Answer:** [RECOMMENDED] ليس official project task في MVP؛ يمكنه request/add personal notes.
- هل assignment لشخص واحد أم multiple؟
  - **Recommended Answer:** [RECOMMENDED] primary assignee واحد، ويمكن collaborators كحقل منفصل.
- هل task points موجودة؟
  - **Recommended Answer:** [RECOMMENDED] نعم، points تقديرية تساعد capacity/performance، وليست وحدها معيار النجاح.
- هل priority؟
  - **Recommended Answer:** [RECOMMENDED] نعم.
- هل labels؟
  - **Recommended Answer:** [RECOMMENDED] نعم basic labels.
- هل dependencies؟
  - **Recommended Answer:** [RECOMMENDED] نعم للمهام التي تعتمد على بعضها، لأنها تحاكي بيئة العمل الحقيقية.
- هل task comments؟
  - **Recommended Answer:** [RECOMMENDED] نعم.
- هل task history/audit؟
  - **Recommended Answer:** [RECOMMENDED] نعم للstatus/assignee/due date changes.
- هل mentor يستطيع reassign؟
  - **Recommended Answer:** [RECOMMENDED] نعم.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- ماذا يحدث إذا member ترك team؟
  - **Recommended Answer:** [RECOMMENDED] open tasks تُعاد توزيعها، والـhistory تبقى منسوبة لصاحبها السابق.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.

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
  - **Recommended Answer:** [RECOMMENDED] multiple versions، مع واحدة current/final.
- هل كل rejection يحتاج feedback؟
  - **Recommended Answer:** [RECOMMENDED] نعم، حتى يكون الرفض تعليمياً وليس مجرد status.
- هل mentor يستطيع approve مباشرة؟
  - **Recommended Answer:** [RECOMMENDED] نعم ضمن صلاحياته، مع audit.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل Admin يستطيع override؟
  - **Recommended Answer:** [RECOMMENDED] نعم مع reason.
- هل final submission versioned؟
  - **Recommended Answer:** [RECOMMENDED] نعم immutable versions.
- هل student يستطيع تعديل بعد submission؟
  - **Recommended Answer:** [RECOMMENDED] لا النسخة المرسلة؛ ينشئ revision جديدة بعد rejection/request changes.
- هل review SLA؟
  - **Recommended Answer:** [RECOMMENDED] نعم target مثل 24–48 ساعة في business policy، مع monitoring وليس وعداً مطلقاً إذا الموارد محدودة.
- هل attachments stored in object storage؟
  - **Recommended Answer:** [RECOMMENDED] نعم، SQL metadata + object storage.

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
  - **Recommended Answer:** [RECOMMENDED] Recommendation MVP: delivery/tasks 25%, technical quality 30%, project outcome 20%, teamwork/communication 15%, consistency/attendance 10%. تُضبط بعد pilot.
- هل AI يدخل في final score؟
  - **Recommended Answer:** [RECOMMENDED] لا كعامل حاسم. AI يمكنه assist/flag، لكن evidence البشري والـbackend rules أساس النتيجة.
- هل mentor score يدخل؟
  - **Recommended Answer:** [RECOMMENDED] نعم بوزن meaningful لكن محدود لتقليل subjectivity.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل attendance؟
  - **Recommended Answer:** [RECOMMENDED] نعم كـengagement signal صغير، وليس بديلاً عن competency.
- هل task completion؟
  - **Recommended Answer:** [RECOMMENDED] نعم، لكن quality أهم من quantity.
- هل code quality؟
  - **Recommended Answer:** [RECOMMENDED] نعم للـtechnical tracks عبر rubric.
- هل peer evaluation؟
  - **Recommended Answer:** [RECOMMENDED] optional/low weight في MVP، لأن bias يحتاج calibration.
- هل final assessment؟
  - **Recommended Answer:** [RECOMMENDED] نعم إذا كان له معنى واضح: final project/demo/assessment مرتبط بالـTrack.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل student يستطيع appeal؟
  - **Recommended Answer:** [RECOMMENDED] نعم خلال نافذة زمنية قصيرة، مع review مستقل.
- هل Admin override؟
  - **Recommended Answer:** [RECOMMENDED] يُحسم بنفس business rule الموجودة في القسم الرئيسي، ويجب تسجيل القرار في Decision Log قبل التنفيذ.
- هل final score versioned؟
  - **Recommended Answer:** [RECOMMENDED] نعم، كل recalculation/override version جديدة.

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
  - **Recommended Answer:** [RECOMMENDED] لا. access حسب package/track/entitlements، مع preview محدود لزيادة conversion.
- أم package-based؟
  - **Recommended Answer:** [RECOMMENDED] نعم، package-based مع entitlement model.
- هل standalone courses في MVP؟
  - **Recommended Answer:** [RECOMMENDED] ليس كمنتج أساسي في البداية؛ يمكن دعم catalog لكن البيع الفردي Phase 2 إذا كان سيعقد pricing.
- هل course progress ينتقل بين enrollments؟
  - **Recommended Answer:** [RECOMMENDED] progress على مستوى user/course، ويُحافظ عليه إذا كان course مشتركاً ومسموحاً به.
- ماذا يحدث بعد refund؟
  - **Recommended Answer:** [RECOMMENDED] access يُلغى، وأي certificate مرتبط بإنجاز تم إلغاؤه يُراجع وفق policy؛ لا نحذف السجل.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل lesson download؟
  - **Recommended Answer:** [RECOMMENDED] لا افتراضياً في MVP؛ streaming/protected access أفضل للتحكم في المحتوى.
- هل quiz attempts limited؟
  - **Recommended Answer:** [RECOMMENDED] نعم، 2–3 attempts حسب نوع quiz، مع إمكانية retake policy.
- هل course completion prerequisite للInternship؟
  - **Recommended Answer:** [RECOMMENDED] فقط prerequisites الضرورية لكل Track؛ لا نجعل كل course completion شرطاً حتى لا نحول المسار إلى bottleneck.
- هل skill gaps recommendations mandatory؟
  - **Recommended Answer:** [RECOMMENDED] recommendations، وليست mandatory إلا للـcritical prerequisites.
- هل Admin يستطيع override recommendation؟
  - **Recommended Answer:** [RECOMMENDED] نعم.

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
  - **Recommended Answer:** [RECOMMENDED] بعض package tiers يمكن أن تتضمن credits، وليس unlimited.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- كم session لكل Package؟
  - **Recommended Answer:** [RECOMMENDED] tier-based: مثال 3M = 1–2، 6M = 3–4، 12M = 6–8، ثم نضبط بالأرقام بعد unit economics.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- duration؟
  - **Recommended Answer:** [RECOMMENDED] 30 أو 60 دقيقة حسب المنتج.
- booking window؟
  - **Recommended Answer:** [RECOMMENDED] الحجز حتى 30 يوماً للأمام، ويُمنع booking المتأخر حسب availability.
- cancellation؟
  - **Recommended Answer:** [RECOMMENDED] 24-hour policy.
- reschedule؟
  - **Recommended Answer:** [RECOMMENDED] مرة واحدة قبل 24 ساعة.
- no-show؟
  - **Recommended Answer:** [RECOMMENDED] student no-show يستهلك credit بعد grace period؛ mentor no-show يعيد credit بالكامل.
- mentor selection؟
  - **Recommended Answer:** [RECOMMENDED] اختيار من available mentors مع filters، وإلا auto-assignment.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- auto assignment؟
  - **Recommended Answer:** [RECOMMENDED] نعم كfallback based on track/skill/capacity.
- notes؟
  - **Recommended Answer:** [RECOMMENDED] نعم.
- rating؟
  - **Recommended Answer:** [RECOMMENDED] نعم.
- time zones؟
  - **Recommended Answer:** [RECOMMENDED] نخزن UTC ونظهر local time للمستخدم.
- ماذا لو booking race condition؟
  - **Recommended Answer:** [RECOMMENDED] transaction + concurrency control + unique constraint على slot/mentor/time.
- هل booking transactionally locks slot؟
  - **Recommended Answer:** [RECOMMENDED] نعم عند confirmation.

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
  - **Recommended Answer:** [RECOMMENDED] team members + assigned mentors/admin support حسب context.
- هل students يقدروا يكلموا خارج team؟
  - **Recommended Answer:** [RECOMMENDED] لا direct messaging مفتوح في MVP؛ يمكن mentoring booking أو support channel.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل former mentor يستطيع messaging؟
  - **Recommended Answer:** [RECOMMENDED] read/history وفق retention، ولا direct new conversation بعد انتهاء العلاقة إلا إذا session جديدة.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- ماذا يحدث بعد expiry؟
  - **Recommended Answer:** [RECOMMENDED] collaboration actions تتوقف، history تبقى للمدة المحددة.
- message retention؟
  - **Recommended Answer:** [RECOMMENDED] retention محددة مثل 12 شهراً أو حسب policy، مع إمكانية archive.
- attachments؟
  - **Recommended Answer:** [RECOMMENDED] basic attachments لاحقاً؛ MVP يركز على text + links لتقليل abuse/storage.
- moderation؟
  - **Recommended Answer:** [RECOMMENDED] report + admin moderation controls؛ automated moderation Phase 2.
- report/block؟
  - **Recommended Answer:** [RECOMMENDED] report متاح؛ block في direct messaging إذا أضيف لاحقاً.
- unread count؟
  - **Recommended Answer:** [RECOMMENDED] نعم.
- notification preferences؟
  - **Recommended Answer:** [RECOMMENDED] نعم لكل channel/category ما عدا critical operational/security messages.
- هل messages قابلة للحذف؟
  - **Recommended Answer:** [RECOMMENDED] student يستطيع delete-for-self إن لزم، لكن audit/retention لا يُمحى من backend فوراً.

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
  - **Recommended Answer:** [RECOMMENDED] In-app + Email في MVP. Push/SMS لاحقاً.
- هل user يستطيع disable email؟
  - **Recommended Answer:** [RECOMMENDED] نعم للـmarketing/non-critical؛ لا للرسائل الضرورية للطلب/الدفع/الأمان.
- هل critical notifications لا يمكن disable؟
  - **Recommended Answer:** [RECOMMENDED] نعم.
- هل notifications لها priority؟
  - **Recommended Answer:** [RECOMMENDED] نعم: Critical / Important / Informational.
- هل duplicate events ممكن؟
  - **Recommended Answer:** [RECOMMENDED] قد تصل تقنياً؛ handler idempotent وdedupe key.
- هل retry؟
  - **Recommended Answer:** [RECOMMENDED] نعم مع exponential backoff وحدود ومحاولة dead-letter عند الفشل المستمر.
- هل notification templates versioned؟
  - **Recommended Answer:** [RECOMMENDED] نعم.
- هل scheduled reminders؟
  - **Recommended Answer:** [RECOMMENDED] نعم للتقييمات، السبرنت، mentoring، والدفع المتأخر.

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
  - **Recommended Answer:** [RECOMMENDED] certificate عند استيفاء completion + evaluation criteria، وليس بمجرد الدفع أو مرور الوقت.
- هل 3/6/12 لها certificates مختلفة؟
  - **Recommended Answer:** [RECOMMENDED] credential type يوضح package/achievement، لكن لا نصنع 3 شهادات شكلية بلا فرق حقيقي.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل Renewal يحصل على certificate؟
  - **Recommended Answer:** [RECOMMENDED] لا تلقائياً؛ certificate جديد فقط إذا تحقق achievement جديد.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل Upgrade يحصل على certificate جديد؟
  - **Recommended Answer:** [RECOMMENDED] فقط إذا نتج عنه achievement إضافي مستوفى.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل certificate Track-specific؟
  - **Recommended Answer:** [RECOMMENDED] نعم.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل Certificate ID؟
  - **Recommended Answer:** [RECOMMENDED] نعم unique ID.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل public verification؟
  - **Recommended Answer:** [RECOMMENDED] نعم صفحة تحقق عامة بأقل قدر من البيانات.
- هل Admin revoke؟
  - **Recommended Answer:** [RECOMMENDED] نعم مع reason/audit.
- ماذا يحدث بعد refund؟
  - **Recommended Answer:** [RECOMMENDED] access يُلغى، وأي certificate مرتبط بإنجاز تم إلغاؤه يُراجع وفق policy؛ لا نحذف السجل.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.

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
  - **Recommended Answer:** [RECOMMENDED] نعم كـpilot محدود، وليس marketplace كامل للشركات. الهدف إثبات placement value دون بناء employer portal.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل 12-month فقط؟
  - **Recommended Answer:** [RECOMMENDED] لا نربطها بالمدة وحدها. الأفضل eligibility-based؛ 12M قد يكون الأكثر شيوعاً لكنه ليس حصرياً.
- minimum score؟
  - **Recommended Answer:** [RECOMMENDED] نعم readiness threshold + minimum critical skills، وتكون thresholds configurable لكل Track.
- internship completion required؟
  - **Recommended Answer:** [RECOMMENDED] نعم للحصول على recommendation مبنية على performance حقيقي.
- mentor score threshold؟
  - **Recommended Answer:** [RECOMMENDED] نعم كإشارة، لكن لا يكون وحده gate.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- portfolio required؟
  - **Recommended Answer:** [RECOMMENDED] نعم للـtechnical/creative tracks عندما يكون portfolio جزءاً من طبيعة الدور؛ beginner path يمكن أن يستخدم project evidence بدلاً منه.
- student opt-in؟
  - **Recommended Answer:** [RECOMMENDED] نعم.
- consent؟
  - **Recommended Answer:** [RECOMMENDED] explicit consent قبل مشاركة profile/CV/portfolio مع employer.
- ما data التي يتم مشاركتها؟
  - **Recommended Answer:** [RECOMMENDED] minimum relevant data: name, role/track, skills, verified projects, evaluation summary, CV/portfolio إذا وافق. لا نشارك بيانات حساسة غير لازمة.
- مع كم Company؟
  - **Recommended Answer:** [RECOMMENDED] batch محدود/محدد لكل student في البداية، وليس نشر profile علناً.
- automatic أم admin reviewed؟
  - **Recommended Answer:** [RECOMMENDED] Admin reviewed في MVP بعد rule-based eligibility + AI assistance.
- هل company تستطيع reject؟
  - **Recommended Answer:** [RECOMMENDED] نعم؛ rejection لا يعاقب الطالب ونستخدم feedback إن توفر لتحسين matching.
- هل interview guaranteed؟
  - **Recommended Answer:** [RECOMMENDED] لا. يمكن ضمان eligibility/recommendation فقط، وليس مقابلة شركة.
- Job guaranteed؟ **No**
  - **Recommended Answer:** [DECIDED] لا يوجد Job Guarantee.
- كيف نقيس success؟
  - **Recommended Answer:** [RECOMMENDED] recommendation-to-interview rate، interview rate، offer rate عندما تتوفر، time-to-opportunity، employer satisfaction، student satisfaction.

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
  - **Recommended Answer:** [RECOMMENDED] authorized Product/Business + Finance role، وليس كل Admin.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- من يستطيع Refund؟
  - **Recommended Answer:** [RECOMMENDED] Finance أو privileged Admin وفق threshold.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- من يستطيع change Track؟
  - **Recommended Answer:** [RECOMMENDED] support/admin حسب نقطة lifecycle.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- من يستطيع change Level؟
  - **Recommended Answer:** [RECOMMENDED] Admin/Assessment owner فقط، مع reason.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- من يستطيع move Team؟
  - **Recommended Answer:** [RECOMMENDED] Internship Admin/Operations role.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- من يستطيع manually activate Enrollment؟
  - **Recommended Answer:** [RECOMMENDED] Finance/Operations privileged role، للحالات الاستثنائية فقط.
- من يستطيع edit Payment؟
  - **Recommended Answer:** [RECOMMENDED] لا يتم edit للـfinancial transaction نفسها؛ correction عبر adjustment/reconciliation records.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل كل override يحتاج reason؟
  - **Recommended Answer:** [RECOMMENDED] نعم لكل business override.
- هل كل override audit logged؟
  - **Recommended Answer:** [RECOMMENDED] نعم.
- هل Finance منفصل؟
  - **Recommended Answer:** [RECOMMENDED] نعم من حيث permissions على الأقل.
- هل Admin يرى CV؟
  - **Recommended Answer:** [RECOMMENDED] فقط الأدوار التي تحتاجه، مع least privilege.
- هل Admin يستطيع access private files؟
  - **Recommended Answer:** [RECOMMENDED] فقط بإذن role-based ولغرض تشغيلي واضح، وكل access حساس يسجل.

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
  - **Recommended Answer:** [RECOMMENDED] S3-compatible/cloud object storage للملفات الكبيرة؛ SQL يحتفظ metadata فقط.
- max file size؟
  - **Recommended Answer:** [RECOMMENDED] limits حسب النوع، مثلاً CV 10MB وattachments 25–50MB، قابلة للتهيئة.
- allowed MIME types؟
  - **Recommended Answer:** [RECOMMENDED] allowlist فقط: PDF/DOCX/images حسب الحاجة، لا extension trust.
- antivirus scanning؟
  - **Recommended Answer:** [RECOMMENDED] نعم قبل إتاحة الملفات للآخرين، خاصة attachments.
- signed URLs؟
  - **Recommended Answer:** [RECOMMENDED] نعم للملفات الخاصة.
- expiration؟
  - **Recommended Answer:** [RECOMMENDED] signed URLs قصيرة العمر، مثل 5–15 دقيقة.
- access control؟
  - **Recommended Answer:** [RECOMMENDED] resource-level authorization قبل إصدار الرابط.
- public/private؟
  - **Recommended Answer:** [RECOMMENDED] private by default؛ public فقط certificates verification metadata.
- backup؟
  - **Recommended Answer:** [RECOMMENDED] object versioning/backup حسب criticality.
- retention؟
  - **Recommended Answer:** [RECOMMENDED] retention حسب نوع الملف والغرض، لا forever by default.
- deletion policy؟
  - **Recommended Answer:** [RECOMMENDED] user deletion request يطلق policy-based deletion مع حفظ ما يلزم قانونياً/مالياً.

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
  - **Recommended Answer:** [RECOMMENDED] الطالب + AI processing service عند consent + mentor/authorized staff عند الحاجة. Employer فقط بعد explicit opt-in.
- هل AI يستطيع الوصول إلى CV؟
  - **Recommended Answer:** [RECOMMENDED] نعم فقط أثناء CV parsing/assessment وبأقل صلاحيات ممكنة، مع consent وسياسة retention واضحة.
- هل Mentor يستطيع رؤية CV؟
  - **Recommended Answer:** [RECOMMENDED] نعم إذا كان مفيداً للتوجيه، لكن access محدود.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- هل Student يستطيع delete CV؟
  - **Recommended Answer:** [RECOMMENDED] نعم، ما لم يكن مرتبطاً بسجل قانوني/assessment مطلوب الاحتفاظ به؛ نستخدم delete/deactivate policy.
- Account deletion؟
  - **Recommended Answer:** [RECOMMENDED] نعم مع retention للسجلات اللازمة.
- Data retention؟
  - **Recommended Answer:** [RECOMMENDED] policy حسب data class؛ لا retention موحد لكل شيء.
- AI processing consent؟
  - **Recommended Answer:** [RECOMMENDED] نعم explicit consent قبل أول processing غير الضروري.
- Employer sharing consent؟
  - **Recommended Answer:** [RECOMMENDED] explicit opt-in.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- PII encryption؟
  - **Recommended Answer:** [RECOMMENDED] encryption in transit + at rest، وsecrets/keys خارج source control.
- Audit access؟
  - **Recommended Answer:** [RECOMMENDED] كل access/override حساس قابل للتتبع.
- Signed URLs؟
  - **Recommended Answer:** [RECOMMENDED] نعم.
- Data export؟
  - **Recommended Answer:** [RECOMMENDED] نعم على مستوى profile/basic account data، مع asynchronous export للملفات الكبيرة.
- Privacy requirements؟
  - **Recommended Answer:** [RECOMMENDED] privacy-by-design، consent، minimization، deletion/retention، access control، incident process، ومراجعة قانونية قبل launch.

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
  - **Recommended Answer:** [RECOMMENDED] نضع MVP capacity target أولي بناءً على forecast، ثم load-test. لا نبني architecture على رقم تخميني ضخم فقط.
- Peak traffic؟
  - **Recommended Answer:** [RECOMMENDED] load profile حسب launch/cohort/payment windows، مع headroom 2–3x للعمليات الحرجة.
- Peak assessment users؟
  - **Recommended Answer:** [RECOMMENDED] assessments تُجدول/تُحد السرعة عند الحاجة، والAI processing async لتجنب spikes.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- Peak payment callbacks؟
  - **Recommended Answer:** [RECOMMENDED] webhook endpoint stateless + queue/idempotency.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- AI provider quotas؟
  - **Recommended Answer:** [RECOMMENDED] quota-aware throttling + fallback provider/rules + caching where safe.
- CV upload peak؟
  - **Recommended Answer:** [RECOMMENDED] direct-to-object-storage upload + async parsing.
- DB size after 1 year؟
  - **Recommended Answer:** [RECOMMENDED] forecast من events/users/submissions؛ المهم pagination/indexing/retention وليس رقم ثابت.
- SignalR connections؟
  - **Recommended Answer:** [RECOMMENDED] scale-out/backplane أو managed service عند الحاجة، مع persistence خارج SignalR.
- Object storage growth؟
  - **Recommended Answer:** [RECOMMENDED] lifecycle policies + compression/retention + quotas per user/product.
- RPO؟
  - **Recommended Answer:** [RECOMMENDED] هدف MVP عملي: <= 15–60 دقيقة للبيانات الحرجة حسب تكلفة البنية.
- RTO؟
  - **Recommended Answer:** [RECOMMENDED] هدف MVP: <= 2–4 ساعات للـcritical service، يتحسن مع maturity.
- Backup retention؟
  - **Recommended Answer:** [RECOMMENDED] daily/point-in-time حسب provider، مع restore tests دورية.
- Autoscaling؟
  - **Recommended Answer:** [RECOMMENDED] API/workers scale horizontally عندما metrics تبرر؛ لا autoscaling عشوائي.
- Cost ceiling؟
  - **Recommended Answer:** [RECOMMENDED] نضع monthly budget per active student + alert thresholds، لأن unit economics أهم من infrastructure vanity.

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
  - **Recommended Answer:** [RECOMMENDED] يُحسم بنفس business rule الموجودة في القسم الرئيسي، ويجب تسجيل القرار في Decision Log قبل التنفيذ.
- Phone verification؟
  - **Recommended Answer:** [RECOMMENDED] يُحسم بنفس business rule الموجودة في القسم الرئيسي، ويجب تسجيل القرار في Decision Log قبل التنفيذ.
- CV multiple versions؟
  - **Recommended Answer:** [RECOMMENDED] يُحسم بنفس business rule الموجودة في القسم الرئيسي، ويجب تسجيل القرار في Decision Log قبل التنفيذ.
- Profile required fields؟
  - **Recommended Answer:** [RECOMMENDED] يُحسم بنفس business rule الموجودة في القسم الرئيسي، ويجب تسجيل القرار في Decision Log قبل التنفيذ.
- Account deletion؟
  - **Recommended Answer:** [RECOMMENDED] نعم مع retention للسجلات اللازمة.

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
  - **Recommended Answer:** [RECOMMENDED] Package + Track context، مع entitlement-based access. السعر النهائي package-driven في MVP لتبسيط البيع.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- Track + Package pricing؟
  - **Recommended Answer:** [RECOMMENDED] نفصل Track عن Package domain، لكن checkout يعرض price واضحة للـpackage داخل track context.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- Package fixed price؟
  - **Recommended Answer:** [RECOMMENDED] نعم في MVP لكل package tier، مع price snapshots وpromo rules.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- Entitlements final؟
  - **Recommended Answer:** [RECOMMENDED] نعم قبل Sprint التنفيذ؛ أي تغيير بعد ذلك versioned.

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
  - **Recommended Answer:** [RECOMMENDED] نختار gateway يدعم البطاقات وطرق الدفع المحلية مثل wallets/Fawry حسب availability والتكلفة. القرار النهائي بعد مقارنة fees, settlement, webhooks, refunds, support.
- Refund policy؟
  - **Recommended Answer:** [RECOMMENDED] نفس Refund Policy المركزية في قسم Payments/Refunds؛ لا نخلق policy مختلفة لكل sprint.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- Package duration starts when؟
  - **Recommended Answer:** [RECOMMENDED] تبدأ عند activation بعد successful verified payment، مع preparation-specific policy إذا احتاجها business.
- Order expiration؟
  - **Recommended Answer:** [RECOMMENDED] 24 ساعة افتراضياً للـpending order، configurable.
- Promo codes؟
  - **Recommended Answer:** [RECOMMENDED] نعم لكن بسيستم بسيط: validity, usage limit, package/track scope, max discount, audit.

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
  - **Recommended Answer:** [RECOMMENDED] Attempt أساسي + Retake محدود، مع versioned results وhuman fallback.
- Retake؟
  - **Recommended Answer:** [RECOMMENDED] Attempt أساسي + Retake محدود، مع versioned results وhuman fallback.
- Human fallback؟
  - **Recommended Answer:** [RECOMMENDED] نعم للحالات borderline وAI/provider failure.
- AI-generated questions؟
  - **Recommended Answer:** [RECOMMENDED] Core MVP يعتمد question bank منظم؛ AI يمكنه التوليد/التكييف داخل حدود template لاحقاً. لا نعتمد على generation الحر وحده في قرار تجاري.
- Score formula؟
  - **Recommended Answer:** [RECOMMENDED] نبدأ بوزن واضح وقابل للتفسير: technical/skill competency هو الأعلى، ثم problem solving، ثم communication/behavioral. التفاصيل تُضبط لكل Track عبر rubric.

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
  - **Recommended Answer:** [RECOMMENDED] Configurable per project template، مع default ثابت في MVP.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- Incomplete team؟
  - **Recommended Answer:** [RECOMMENDED] يُحسم بنفس business rule الموجودة في القسم الرئيسي، ويجب تسجيل القرار في Decision Log قبل التنفيذ.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- Student team change؟
  - **Recommended Answer:** [RECOMMENDED] يُحسم بنفس business rule الموجودة في القسم الرئيسي، ويجب تسجيل القرار في Decision Log قبل التنفيذ.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- Mentor capacity؟
  - **Recommended Answer:** [RECOMMENDED] Capacity limit إلزامي، ويُستخدم كconstraint في assignment.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- AI override؟
  - **Recommended Answer:** [RECOMMENDED] AI recommendation لا تكون final authority؛ Admin override مسموح مع reason/audit.

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
  - **Recommended Answer:** [RECOMMENDED] نعم، duration tiers واضحة.
  - **Business Guardrail:** Keep the rule simple, measurable, auditable, and fair to the student.
- Credits؟
  - **Recommended Answer:** [RECOMMENDED] Credit-based وليس unlimited، مع expiry وusage ledger.
- Cancellation؟
  - **Recommended Answer:** [RECOMMENDED] يُحسم بنفس business rule الموجودة في القسم الرئيسي، ويجب تسجيل القرار في Decision Log قبل التنفيذ.
- Recording؟
  - **Recommended Answer:** [RECOMMENDED] لا في Core MVP افتراضياً؛ يقلل privacy/storage complexity. يمكن تفعيله لاحقاً لبعض products.
- Standalone purchase؟
  - **Recommended Answer:** [RECOMMENDED] نعم حتى غير enrolled، لأن standalone mentoring قناة revenue مستقلة.

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

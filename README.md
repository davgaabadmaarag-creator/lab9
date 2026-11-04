# Лаборатори 9 — Эмнэлгийн цаг захиалгын систем

## Өгүүлбэр бүрийн давхарга

1. `Patient`, `Doctor`, `Appointment` ангиуд байна. — **Domain**
2. Цаг `OPEN`, `BOOKED`, `CANCELLED` төлөвтэй байна. — **Domain**
3. Нэг эмч нэг цагт хоёр өвчтөн авахгүй. — **Domain** (давхаргын бизнесийн дүрэм)
4. Зөвхөн `OPEN` цаг захиалж, төлөвийг `BOOKED` болгоно. — **Domain**
5. Эмч шалгах → сул цаг олох → төлөв өөрчлөх → хадгалах үйлдлийн дараалал. — **Business/Application**
6. Өвчтөн, эмч, захиалгыг хадгалах, хайх. — **Infrastructure** (репозиторийн интерфэйс нь Application-д байна)
7. Хүсэлтийг хүлээн авч, `appointmentId`-тай хариу өгөх. — **Presentation**
8. Шаардлагатай талбар дутуу үед HTTP 400 буцаах. — **Presentation**

## Давхаргын бүтэц

```text
lab9/
├── domain/                         # Entity, төлөв, бизнесийн дүрэм
│   ├── Appointment.ts
│   ├── AppointmentSchedulingPolicy.ts
│   ├── Doctor.ts
│   └── Patient.ts
├── application/                    # Захиалгын use case ба repository port
│   ├── errors/
│   ├── ports/
│   └── services/
├── infrastructure/                 # In-memory repository implementation
├── presentation/                    # UI, HTTP API handler, stylesheet
│   ├── pages/
│   │   └── api/
│   └── styles/
├── pages/                           # Next.js Pages Router entry points
│   └── api/
├── next.config.ts
└── tsconfig.json
```

Энэ лабораторийн өгөгдөл `InMemoryClinicRepository`-д хадгалагдана. Серверийг дахин эхлүүлэхэд туршилтын өгөгдөл анхны төлөвтөө орно.

## Ажиллуулах

Төслийн үндсэн хавтаснаас:

```bash
npm run dev:lab9
```

Дараа нь `http://localhost:3000` хаягийг нээнэ. API нь `GET /api/appointments` болон `POST /api/appointments` endpoint-той.

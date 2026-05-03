# site-cha-casa-nova
Aniversário/ chá de casa nova Gabriella e import { useEffect, useState } from "react";

import {

  Calendar,

  Clock,

  Gift,

  Heart,

  MapPin,

  Mail,

  User,

} from "lucide-react";

const eventDate = new Date("2026-06-28T12:00:00");

const gifts = [

  {

    name: "Jogo de Panelas",

    price: "R$ 399,90",

    purchaseLink: "https://seusite.com/panelas",

  },

  {

    name: "Air Fryer",

    price: "R$ 599,90",

    purchaseLink: "https://seusite.com/airfryer",

  },

  {

    name: "Jogo de Toalhas",

    price: "R$ 149,90",

    purchaseLink: "https://seusite.com/toalhas",

  },

  {

    name: "Cota Decoração",

    price: "R$ 100,00",

    purchaseLink: "#",

  },

];

export default function HomePage() {

  return (

    <main className="bg-[#F5F3EE] text-[#3E4A54]">

      <Hero />

      <Countdown />

      <About />

      <Journey />

      <GiftList />

      <RSVP />

      <Location />

      <Footer />

    </main>

  );

}

function Hero() {

  return (

    <section className="relative flex min-h-screen items-center justify-center px-6 text-center">

      <div className="absolute inset-0 bg-[#1E2B3D]" />

      <div className="relative z-10 max-w-4xl text-white">

        <p className="mb-4 text-sm uppercase tracking-[0.3em] text-[#A9B4BF]">

          Aniversário + Chá de Casa Nova

        </p>

        <h1 className="font-serif text-6xl md:text-8xl">

          Gabriella & Igor

        </h1>

        <p className="mx-auto mt-8 max-w-2xl text-lg leading-8 md:text-xl">

          Cada passo nos trouxe até aqui. Bem-vindos ao nosso novo começo.

        </p>

      </div>

    </section>

  );

}

function Countdown() {

  const [timeLeft, setTimeLeft] = useState(getTimeLeft());

  useEffect(() => {

    const timer = setInterval(() => {

      setTimeLeft(getTimeLeft());

    }, 1000);

    return () => clearInterval(timer);

  }, []);

  return (

    <section className="-mt-16 relative z-20 mx-auto max-w-5xl px-6">

      <div className="grid rounded-3xl bg-white p-8 shadow-xl md:grid-cols-4">

        <CountdownItem value={timeLeft.days} label="Dias" />

        <CountdownItem value={timeLeft.hours} label="Horas" />

        <CountdownItem value={timeLeft.minutes} label="Min" />

        <CountdownItem value={timeLeft.seconds} label="Seg" />

      </div>

    </section>

  );

}

function About() {

  return (

    <section className="mx-auto max-w-5xl px-6 py-24 text-center">

      <h2 className="font-serif text-4xl text-[#1E2B3D]">

        Nosso Novo Capítulo

      </h2>

      <p className="mx-auto mt-6 max-w-3xl leading-8">

        Entre sonhos, planos e caixas de mudança, queremos celebrar

        esse momento especial com pessoas importantes em nossa vida.

      </p>

    </section>

  );

}

function Journey() {

  return (

    <section className="bg-white py-24">

      <div className="mx-auto max-w-5xl px-6 text-center">

        <Heart className="mx-auto mb-4 text-[#5A3A29]" />

        <h2 className="font-serif text-4xl text-[#1E2B3D]">

          Nossa Jornada

        </h2>

        <div className="mt-12 grid gap-6 md:grid-cols-3">

          <JourneyCard title="Como nos conhecemos" />

          <JourneyCard title="Momentos especiais" />

          <JourneyCard title="Nosso novo lar" />

        </div>

      </div>

    </section>

  );

}

function GiftList() {

  return (

    <section className="py-24">

      <div className="mx-auto max-w-6xl px-6">

        <div className="text-center">

          <Gift className="mx-auto mb-4 text-[#5A3A29]" />

          <h2 className="font-serif text-4xl text-[#1E2B3D]">

            Lista de Presentes

          </h2>

        </div>

        <div className="mt-12 grid gap-6 md:grid-cols-2">

          {gifts.map((gift) => (

            <div

              key={gift.name}

              className="rounded-3xl border border-[#A9B4BF]/20 bg-white p-8 shadow-sm"

            >

              <h3 className="font-serif text-2xl text-[#1E2B3D]">

                {gift.name}

              </h3>

              <p className="mt-3">{gift.price}</p>

              <div className="mt-6 flex flex-col gap-3">

                <button className="rounded-xl bg-[#1E2B3D] px-6 py-3 text-white">

                  Reservar para entregar no dia

                </button>

                <button className="rounded-xl border border-[#1E2B3D] px-6 py-3">

                  Pagar via Pix

                </button>

                <a

                  href={gift.purchaseLink}

                  className="rounded-xl border border-[#A9B4BF] px-6 py-3 text-center"

                >

                  Comprar online

                </a>

              </div>

            </div>

          ))}

        </div>

      </div>

    </section>

  );

}

function RSVP() {

  return (

    <section className="bg-white py-24">

      <div className="mx-auto max-w-3xl rounded-3xl p-10 shadow-lg">

        <h2 className="mb-8 text-center font-serif text-4xl text-[#1E2B3D]">

          Confirmar presença

        </h2>

        <form className="space-y-4">

          <Input icon={<User size={18} />} placeholder="Nome" />

          <Input icon={<Mail size={18} />} placeholder="E-mail" />

          <Input placeholder="Vai comparecer?" />

          <Input placeholder="Número de acompanhantes" />

          <button className="w-full rounded-xl bg-[#1E2B3D] py-4 text-white">

            Confirmar presença

          </button>

        </form>

      </div>

    </section>

  );

}

function Location() {

  return (

    <section className="py-24 text-center">

      <MapPin className="mx-auto mb-4 text-[#5A3A29]" />

      <h2 className="font-serif text-4xl text-[#1E2B3D]">Localização</h2>

      <p className="mt-4">Local em definição • Em breve atualizaremos</p>

    </section>

  );

}

function Footer() {

  return (

    <footer className="border-t border-[#A9B4BF]/20 py-10 text-center">

      <p>Gabriella & Igor • 28.06.2026</p>

    </footer>

  );

}

function CountdownItem({

  value,

  label,

}: {

  value: number;

  label: string;

}) {

  return (

    <div className="text-center">

      <p className="font-serif text-4xl text-[#1E2B3D]">{value}</p>

      <p className="mt-2 text-sm uppercase tracking-widest">{label}</p>

    </div>

  );

}

function JourneyCard({ title }: { title: string }) {

  return (

    <div className="rounded-3xl border border-[#A9B4BF]/20 p-8">

      <p>{title}</p>

    </div>

  );

}

function Input({

  placeholder,

  icon,

}: {

  placeholder: string;

  icon?: React.ReactNode;

}) {

  return (

    <div className="flex items-center gap-3 rounded-xl border border-[#A9B4BF]/20 p-4">

      {icon}

      <input

        placeholder={placeholder}

        className="w-full bg-transparent outline-none"

      />

    </div>

  );

}

function getTimeLeft() {

  const difference = +eventDate - +new Date();

  return {

    days: Math.max(0, Math.floor(difference / (1000 * 60 * 60 * 24))),

    hours: Math.max(0, Math.floor((difference / (1000 * 60 * 60)) % 24)),

    minutes: Math.max(0, Math.floor((difference / 1000 / 60) % 60)),

    seconds: Math.max(0, Math.floor((difference / 1000) % 60)),

  };

}

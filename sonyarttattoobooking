import React, { useState } from 'react';
import { Calendar } from '@/components/ui/calendar';
import { Card, CardHeader, CardContent } from '@/components/ui/card';
import { Check, CalendarDays, LogIn } from 'lucide-react';

const TattooBookingApp = () => {
  const [currentPage, setCurrentPage] = useState('home');
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    phone: '',
    projectType: '',
    description: '',
    date: null,
    time: ''
  });

  const timeSlots = ['10:00', '11:00', '12:00', '14:00', '15:00', '16:00', '17:00'];

  const HomePage = () => {
    return (
      <div className="min-h-screen bg-white">
        <div className="max-w-4xl mx-auto p-6">
          <h1 className="text-4xl font-bold text-center mb-8">Sonyarttattoo</h1>
          <div className="grid md:grid-cols-2 gap-6">
            <Card 
              className="cursor-pointer hover:shadow-lg transition-shadow"
              onClick={() => setCurrentPage('booking')}
            >
              <CardHeader className="text-center">
                <CalendarDays className="w-12 h-12 mx-auto mb-4" />
                <h2 className="text-2xl font-semibold">Réserver un rendez-vous</h2>
                <p className="text-gray-600">Planifiez votre prochain tatouage</p>
              </CardHeader>
            </Card>

            <Card 
              className="cursor-pointer hover:shadow-lg transition-shadow"
              onClick={() => setCurrentPage('admin-login')}
            >
              <CardHeader className="text-center">
                <LogIn className="w-12 h-12 mx-auto mb-4" />
                <h2 className="text-2xl font-semibold">Administration</h2>
                <p className="text-gray-600">Accès réservé</p>
              </CardHeader>
            </Card>
          </div>
        </div>
      </div>
    );
  };

  const BookingPage = () => {
    const handleSubmit = (e) => {
      e.preventDefault();
      setCurrentPage('confirmation');
    };

    return (
      <div className="max-w-4xl mx-auto p-6">
        <h1 className="text-3xl font-bold text-center mb-8">Réserver un rendez-vous</h1>
        
        <form onSubmit={handleSubmit} className="grid md:grid-cols-2 gap-6">
          <Card>
            <CardHeader>
              <h2 className="text-xl font-semibold">Informations personnelles</h2>
            </CardHeader>
            <CardContent>
              <div className="space-y-4">
                <div>
                  <label className="block mb-2">Nom complet *</label>
                  <input
                    type="text"
                    required
                    className="w-full p-2 border rounded-lg"
                    value={formData.name}
                    onChange={(e) => setFormData({...formData, name: e.target.value})}
                  />
                </div>
                <div>
                  <label className="block mb-2">Email *</label>
                  <input
                    type="email"
                    required
                    className="w-full p-2 border rounded-lg"
                    value={formData.email}
                    onChange={(e) => setFormData({...formData, email: e.target.value})}
                  />
                </div>
                <div>
                  <label className="block mb-2">Téléphone *</label>
                  <input
                    type="tel"
                    required
                    className="w-full p-2 border rounded-lg"
                    value={formData.phone}
                    onChange={(e) => setFormData({...formData, phone: e.target.value})}
                  />
                </div>
              </div>
            </CardContent>
          </Card>

          <Card>
            <CardHeader>
              <h2 className="text-xl font-semibold">Votre projet</h2>
            </CardHeader>
            <CardContent>
              <div className="space-y-4">
                <div>
                  <label className="block mb-2">Type de projet *</label>
                  <select
                    required
                    className="w-full p-2 border rounded-lg"
                    value={formData.projectType}
                    onChange={(e) => setFormData({...formData, projectType: e.target.value})}
                  >
                    <option value="">Sélectionnez un type</option>
                    <option value="realiste">Réaliste</option>
                    <option value="traditionnel">Traditionnel</option>
                    <option value="japonais">Japonais</option>
                    <option value="ornemental">Ornemental</option>
                  </select>
                </div>
                <div>
                  <label className="block mb-2">Description du projet *</label>
                  <textarea
                    required
                    className="w-full p-2 border rounded-lg h-32"
                    value={formData.description}
                    onChange={(e) => setFormData({...formData, description: e.target.value})}
                    placeholder="Décrivez votre projet en détail..."
                  />
                </div>
              </div>
            </CardContent>
          </Card>

          <Card className="md:col-span-2">
            <CardHeader>
              <h2 className="text-xl font-semibold">Sélectionnez une date et un horaire</h2>
            </CardHeader>
            <CardContent>
              <div className="grid md:grid-cols-2 gap-6">
                <div>
                  <Calendar
                    mode="single"
                    selected={formData.date}
                    onSelect={(date) => setFormData({...formData, date})}
                    disabled={(date) => {
                      const today = new Date();
                      today.setHours(0, 0, 0, 0);
                      return date < today;
                    }}
                    className="rounded-md border"
                  />
                </div>

                <div>
                  <label className="block mb-2">Horaire disponible *</label>
                  <div className="grid grid-cols-2 gap-2">
                    {timeSlots.map((time) => (
                      <button
                        key={time}
                        type="button"
                        className={`p-2 border rounded-lg ${
                          formData.time === time 
                            ? 'bg-black text-white' 
                            : 'hover:bg-gray-100'
                        }`}
                        onClick={() => setFormData({...formData, time})}
                      >
                        {time}
                      </button>
                    ))}
                  </div>
                </div>
              </div>
            </CardContent>
          </Card>

          <div className="md:col-span-2">
            <button
              type="submit"
              className="w-full p-3 rounded-lg bg-black text-white hover:bg-gray-800 transition-colors"
            >
              Valider la demande de rendez-vous
            </button>
          </div>
        </form>
      </div>
    );
  };

  const ConfirmationPage = () => {
    return (
      <div className="min-h-screen bg-gray-50 py-12 px-4">
        <div className="max-w-3xl mx-auto">
          <Card className="bg-white shadow-xl">
            <CardHeader className="bg-green-50 border-b pb-6">
              <div className="flex items-center justify-center mb-4">
                <div className="bg-green-500 rounded-full p-2">
                  <Check className="h-8 w-8 text-white" />
                </div>
              </div>
              <h2 className="text-3xl font-bold text-center text-green-800">
                Demande envoyée avec succès !
              </h2>
            </CardHeader>
            <CardContent className="p-8">
              <div className="space-y-6">
                <div>
                  <h3 className="text-xl font-semibold mb-4">Détails de votre rendez-vous</h3>
                  <div className="grid gap-4">
                    <div className="bg-gray-50 p-4 rounded-lg">
                      <p className="text-sm text-gray-600">Nom</p>
                      <p className="font-medium">{formData.name}</p>
                    </div>
                    <div className="bg-gray-50 p-4 rounded-lg">
                      <p className="text-sm text-gray-600">Email</p>
                      <p className="font-medium">{formData.email}</p>
                    </div>
                    <div className="bg-gray-50 p-4 rounded-lg">
                      <p className="text-sm text-gray-600">Téléphone</p>
                      <p className="font-medium">{formData.phone}</p>
                    </div>
                    <div className="bg-gray-50 p-4 rounded-lg">
                      <p className="text-sm text-gray-600">Date et heure</p>
                      <p className="font-medium">
                        {formData.date?.toLocaleDateString('fr-FR')} à {formData.time}
                      </p>
                    </div>
                    <div className="bg-gray-50 p-4 rounded-lg">
                      <p className="text-sm text-gray-600">Type de projet</p>
                      <p className="font-medium">{formData.projectType}</p>
                    </div>
                    <div className="bg-gray-50 p-4 rounded-lg">
                      <p className="text-sm text-gray-600">Description</p>
                      <p className="font-medium">{formData.description}</p>
                    </div>
                  </div>
                </div>
                <div className="flex justify-center gap-4">
                  <button
                    onClick={() => setCurrentPage('home')}
                    className="bg-black text-white px-6 py-3 rounded-lg hover:bg-gray-800"
                  >
                    Retour à l'accueil
                  </button>
                </div>
              </div>
            </CardContent>
          </Card>
        </div>
      </div>
    );
  };

  switch (currentPage) {
    case 'booking':
      return <BookingPage />;
    case 'confirmation':
      return <ConfirmationPage />;
    default:
      return <HomePage />;
  }
};

export default TattooBookingApp;

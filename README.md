import React, { useState, useEffect } from "react";
import {
  Plus,
  Package,
  DollarSign,
  Users,
  FileText,
  Trash2,
  Edit2,
  Download,
  Search,
  Settings,
  User,
  Bell,
  Sun,
  Moon,
  BarChart3,
  Filter,
  X,
} from "lucide-react";

const OrderManagerDemo = () => {
  // États principaux
  const [orders, setOrders] = useState([]);
  const [clients, setClients] = useState([]);
  const [showForm, setShowForm] = useState(false);
  const [editingOrder, setEditingOrder] = useState(null);
  const [currentView, setCurrentView] = useState("dashboard");
  const [shopSettings, setShopSettings] = useState({
    name: "Ma Boutique",
    phone: "+237 6XX XXX XXX",
    address: "Douala, Cameroun",
    signature: "Le Responsable",
  });
  const [searchTerm, setSearchTerm] = useState("");
  const [statusFilter, setStatusFilter] = useState("all");
  const [darkMode, setDarkMode] = useState(false);
  const [showSettings, setShowSettings] = useState(false);
  const [notifications, setNotifications] = useState([]);
  const [itemCount, setItemCount] = useState(1);
  const [showItemForm, setShowItemForm] = useState(false);

  // État du formulaire
  const [formData, setFormData] = useState({
    clientName: "",
    clientPhone: "",
    clientAddress: "",
    items: [],
    status: "pending",
    notes: "",
  });

  // Charger les données depuis le localStorage
  useEffect(() => {
    const savedOrders = localStorage.getItem("orders_demo");
    const savedClients = localStorage.getItem("clients_demo");
    const savedSettings = localStorage.getItem("shopSettings_demo");
    const savedDarkMode = localStorage.getItem("darkMode_demo");

    if (savedOrders) setOrders(JSON.parse(savedOrders));
    if (savedClients) setClients(JSON.parse(savedClients));
    if (savedSettings) setShopSettings(JSON.parse(savedSettings));
    if (savedDarkMode) setDarkMode(JSON.parse(savedDarkMode));
  }, []);

  // Sauvegarder les données
  useEffect(() => {
    localStorage.setItem("orders_demo", JSON.stringify(orders));
    localStorage.setItem("clients_demo", JSON.stringify(clients));
    localStorage.setItem("shopSettings_demo", JSON.stringify(shopSettings));
    localStorage.setItem("darkMode_demo", JSON.stringify(darkMode));
  }, [orders, clients, shopSettings, darkMode]);

  // Générer les notifications
  useEffect(() => {
    const pendingOrders = orders.filter((order) => order.status === "pending");
    const newNotifications = pendingOrders.map((order) => ({
      id: Date.now() + Math.random(),
      type: "reminder",
      message: `Rappel: Commande #${order.id} en attente de paiement`,
      orderId: order.id,
      date: new Date().toISOString(),
    }));
    setNotifications(newNotifications);
  }, [orders]);

  // 🔢 FONCTION POUR DEMANDER LE NOMBRE D'ARTICLES
  const handleStartOrder = () => {
    setShowForm(true);
    setEditingOrder(null);
    setFormData({
      clientName: "",
      clientPhone: "",
      clientAddress: "",
      items: [],
      status: "pending",
      notes: "",
    });
    setShowItemForm(false);
    setItemCount(1);
  };

  const confirmItemCount = () => {
    if (itemCount < 1 || itemCount > 50) {
      alert("Veuillez entrer un nombre entre 1 et 50");
      return;
    }

    // Créer le nombre d'articles demandés
    const newItems = Array.from({ length: itemCount }, () => ({
      name: "",
      quantity: 1,
      price: 0,
      stock: 0,
    }));

    setFormData({
      ...formData,
      items: newItems,
    });
    setShowItemForm(true);
  };

  // Fonctions de calcul
  const calculateTotal = (items) => {
    return items.reduce((sum, item) => sum + item.quantity * item.price, 0);
  };

  // 📊 ANALYTIQUES AVANCÉES
  const calculateStats = () => {
    const today = new Date();
    const lastWeek = new Date(today.getTime() - 7 * 24 * 60 * 60 * 1000);
    const lastMonth = new Date(today.getTime() - 30 * 24 * 60 * 60 * 1000);

    const recentOrders = orders.filter(
      (order) => new Date(order.date) > lastMonth
    );
    const weeklyOrders = orders.filter(
      (order) => new Date(order.date) > lastWeek
    );

    // Revenus par jour
    const revenueByDay = {};
    // Commandes par statut
    const ordersByStatus = {
      pending: orders.filter((o) => o.status === "pending").length,
      paid: orders.filter((o) => o.status === "paid").length,
      delivered: orders.filter((o) => o.status === "delivered").length,
    };

    // Revenus par mois
    const revenueByMonth = {};
    // Articles les plus vendus
    const popularItems = {};

    orders.forEach((order) => {
      const date = new Date(order.date);
      const dayKey = date.toLocaleDateString();
      const monthKey = `${date.getMonth() + 1}/${date.getFullYear()}`;

      if (order.status === "paid" || order.status === "delivered") {
        revenueByDay[dayKey] = (revenueByDay[dayKey] || 0) + order.total;
        revenueByMonth[monthKey] =
          (revenueByMonth[monthKey] || 0) + order.total;
      }

      // Compter les articles populaires
      order.items.forEach((item) => {
        popularItems[item.name] =
          (popularItems[item.name] || 0) + item.quantity;
      });
    });

    // Transformer en tableau et trier
    const topItems = Object.entries(popularItems)
      .map(([name, quantity]) => ({ name, quantity }))
      .sort((a, b) => b.quantity - a.quantity)
      .slice(0, 5);

    // Taux de conversion
    const conversionRate =
      orders.length > 0
        ? (
            ((ordersByStatus.paid + ordersByStatus.delivered) / orders.length) *
            100
          ).toFixed(1)
        : 0;

    // Valeur moyenne des commandes
    const averageOrderValue =
      orders.length > 0
        ? orders.reduce((sum, order) => sum + order.total, 0) / orders.length
        : 0;

    return {
      total: orders.length,
      pending: ordersByStatus.pending,
      paid: ordersByStatus.paid,
      delivered: ordersByStatus.delivered,
      revenue: orders
        .filter((o) => o.status === "paid" || o.status === "delivered")
        .reduce((sum, o) => sum + o.total, 0),
      weeklyRevenue: weeklyOrders
        .filter((o) => o.status === "paid" || o.status === "delivered")
        .reduce((sum, o) => sum + o.total, 0),
      revenueByDay,
      revenueByMonth,
      topClients: clients
        .sort((a, b) => b.totalSpent - a.totalSpent)
        .slice(0, 5),
      topItems,
      conversionRate,
      averageOrderValue,
      ordersByStatus,
    };
  };

  // Gestion des articles
  const addItem = () => {
    setFormData({
      ...formData,
      items: [...formData.items, { name: "", quantity: 1, price: 0, stock: 0 }],
    });
  };

  const updateItem = (index, field, value) => {
    const newItems = [...formData.items];
    newItems[index][field] = field === "name" ? value : Number(value);
    setFormData({ ...formData, items: newItems });
  };

  const removeItem = (index) => {
    const newItems = formData.items.filter((_, i) => i !== index);
    setFormData({ ...formData, items: newItems });
  };

  // Soumission du formulaire
  const handleSubmit = () => {
    if (
      !formData.clientName ||
      !formData.clientPhone ||
      !formData.clientAddress
    ) {
      alert("Veuillez remplir tous les champs obligatoires");
      return;
    }

    const hasEmptyItem = formData.items.some(
      (item) => !item.name || item.quantity < 1 || item.price < 0
    );
    if (hasEmptyItem) {
      alert("Veuillez remplir tous les articles correctement");
      return;
    }

    const newOrder = {
      id: editingOrder?.id || Date.now(),
      ...formData,
      total: calculateTotal(formData.items),
      date: editingOrder?.date || new Date().toISOString(),
    };

    // Mettre à jour les clients
    const clientIndex = clients.findIndex(
      (c) => c.phone === formData.clientPhone
    );
    if (clientIndex === -1) {
      setClients([
        ...clients,
        {
          id: Date.now(),
          name: formData.clientName,
          phone: formData.clientPhone,
          address: formData.clientAddress,
          totalOrders: 1,
          totalSpent: newOrder.total,
          firstOrder: new Date().toISOString(),
          lastOrder: new Date().toISOString(),
        },
      ]);
    } else {
      const updatedClients = [...clients];
      updatedClients[clientIndex] = {
        ...updatedClients[clientIndex],
        totalOrders: updatedClients[clientIndex].totalOrders + 1,
        totalSpent: updatedClients[clientIndex].totalSpent + newOrder.total,
        lastOrder: new Date().toISOString(),
      };
      setClients(updatedClients);
    }

    if (editingOrder) {
      setOrders(orders.map((o) => (o.id === editingOrder.id ? newOrder : o)));
    } else {
      setOrders([newOrder, ...orders]);
    }

    setFormData({
      clientName: "",
      clientPhone: "",
      clientAddress: "",
      items: [],
      status: "pending",
      notes: "",
    });
    setShowForm(false);
    setShowItemForm(false);
    setEditingOrder(null);
    setItemCount(1);
  };

  // Fonctions pour la gestion des commandes
  const deleteOrder = (id) => {
    if (confirm("Êtes-vous sûr de vouloir supprimer cette commande ?")) {
      setOrders(orders.filter((o) => o.id !== id));
    }
  };

  const editOrder = (order) => {
    setEditingOrder(order);
    setFormData({
      clientName: order.clientName,
      clientPhone: order.clientPhone,
      clientAddress: order.clientAddress,
      items: order.items,
      status: order.status,
      notes: order.notes || "",
    });
    setShowForm(true);
    setShowItemForm(true);
    setCurrentView("orders");
  };

  const updateStatus = (id, status) => {
    setOrders(orders.map((o) => (o.id === id ? { ...o, status } : o)));
  };

  // Filtrage et recherche
  const filteredOrders = orders.filter((order) => {
    const matchesSearch =
      order.clientName.toLowerCase().includes(searchTerm.toLowerCase()) ||
      order.clientPhone.includes(searchTerm) ||
      order.id.toString().includes(searchTerm);

    const matchesStatus =
      statusFilter === "all" || order.status === statusFilter;

    return matchesSearch && matchesStatus;
  });

  // Export Excel
  const exportToExcel = () => {
    const headers = [
      "ID",
      "Client",
      "Téléphone",
      "Adresse",
      "Total",
      "Statut",
      "Date",
      "Notes",
    ];
    const data = orders.map((order) => [
      order.id,
      order.clientName,
      order.clientPhone,
      order.clientAddress,
      order.total,
      order.status,
      new Date(order.date).toLocaleDateString("fr-FR"),
      order.notes || "",
    ]);

    const csvContent = [headers, ...data]
      .map((row) => row.map((cell) => `"${cell}"`).join(","))
      .join("\n");

    const blob = new Blob([csvContent], { type: "text/csv;charset=utf-8;" });
    const url = URL.createObjectURL(blob);
    const link = document.createElement("a");
    link.href = url;
    link.download = `commandes_${new Date().toISOString().split("T")[0]}.csv`;
    link.click();
  };

  // Génération de PDF améliorée
  const generatePDF = (order) => {
    const content = `
      <!DOCTYPE html>
      <html>
      <head>
        <meta charset="utf-8">
        <title>Facture ${order.id}</title>
        <style>
          body { font-family: Arial, sans-serif; margin: 40px; color: #333; }
          .header { text-align: center; margin-bottom: 30px; border-bottom: 2px solid #333; padding-bottom: 20px; }
          .shop-name { font-size: 24px; font-weight: bold; margin-bottom: 10px; }
          .invoice-title { font-size: 20px; margin: 20px 0; }
          .section { margin: 20px 0; }
          .items-table { width: 100%; border-collapse: collapse; margin: 20px 0; }
          .items-table th, .items-table td { border: 1px solid #ddd; padding: 10px; text-align: left; }
          .items-table th { background-color: #f5f5f5; }
          .total { font-size: 18px; font-weight: bold; text-align: right; margin-top: 20px; }
          .footer { margin-top: 50px; border-top: 1px solid #ddd; padding-top: 20px; }
          .signature { float: right; text-align: center; }
        </style>
      </head>
      <body>
        <div class="header">
          <div class="shop-name">${shopSettings.name}</div>
          <div>${shopSettings.phone} • ${shopSettings.address}</div>
        </div>
        
        <div class="invoice-title">FACTURE N° ${order.id}</div>
        
        <div class="section">
          <strong>Date:</strong> ${new Date(order.date).toLocaleDateString(
            "fr-FR"
          )}<br>
          <strong>Client:</strong><br>
          ${order.clientName}<br>
          ${order.clientPhone}<br>
          ${order.clientAddress}
        </div>
        
        <table class="items-table">
          <thead>
            <tr>
              <th>Article</th>
              <th>Quantité</th>
              <th>Prix unitaire</th>
              <th>Total</th>
            </tr>
          </thead>
          <tbody>
            ${order.items
              .map(
                (item) => `
              <tr>
                <td>${item.name}</td>
                <td>${item.quantity}</td>
                <td>${item.price.toLocaleString()} FCFA</td>
                <td>${(item.quantity * item.price).toLocaleString()} FCFA</td>
              </tr>
            `
              )
              .join("")}
          </tbody>
        </table>
        
        <div class="total">
          TOTAL: ${order.total.toLocaleString()} FCFA
        </div>
        
        ${
          order.notes
            ? `<div class="section"><strong>Notes:</strong><br>${order.notes}</div>`
            : ""
        }
        
        <div class="footer">
          <div class="signature">
            <div>${shopSettings.signature}</div>
            <div style="margin-top: 50px;">Signature</div>
          </div>
        </div>
      </body>
      </html>
    `;

    const blob = new Blob([content], { type: "text/html" });
    const url = URL.createObjectURL(blob);
    const a = document.createElement("a");
    a.href = url;
    a.download = `Facture_${order.id}.html`;
    a.click();
  };

  const stats = calculateStats();

  const StatusBadge = ({ status }) => {
    const colors = {
      pending: darkMode
        ? "bg-orange-900 text-orange-300"
        : "bg-orange-100 text-orange-800",
      paid: darkMode
        ? "bg-green-900 text-green-300"
        : "bg-green-100 text-green-800",
      delivered: darkMode
        ? "bg-blue-900 text-blue-300"
        : "bg-blue-100 text-blue-800",
    };
    const labels = {
      pending: "En attente",
      paid: "Payé",
      delivered: "Livré",
    };
    return (
      <span
        className={`px-3 py-1 rounded-full text-xs font-semibold ${colors[status]}`}
      >
        {labels[status]}
      </span>
    );
  };

  const themeClasses = darkMode
    ? "bg-gray-900 text-white min-h-screen"
    : "bg-gray-50 min-h-screen";

  const cardClasses = darkMode
    ? "bg-gray-800 border-gray-700 text-white"
    : "bg-white border-gray-100";

  const inputClasses = darkMode
    ? "bg-gray-700 border-gray-600 text-white placeholder-gray-400"
    : "bg-white border-gray-300 text-gray-900 placeholder-gray-500";

  // 🎯 BANNIÈRE DÉMO
  const DemoBanner = () => (
    <div className="bg-gradient-to-r from-yellow-400 to-orange-500 text-white py-2 px-4 text-center">
      <div className="max-w-7xl mx-auto flex items-center justify-center space-x-2">
        <span className="font-semibold">🎯 VERSION DÉMONSTRATION</span>
        <span className="text-yellow-100">
          | Application 100% fonctionnelle
        </span>
      </div>
    </div>
  );

  return (
    <div className={themeClasses}>
      <DemoBanner />

      {/* Header */}
      <div
        className={`bg-gradient-to-r from-blue-600 to-blue-800 text-white p-6 shadow-lg ${
          darkMode ? "from-gray-800 to-gray-900" : ""
        }`}
      >
        <div className="max-w-7xl mx-auto flex justify-between items-center">
          <div>
            <h1 className="text-3xl font-bold mb-2">📱 {shopSettings.name}</h1>
            <p className="text-blue-100">
              Gestionnaire de Commandes Professionnel - Version Démo
            </p>
          </div>
          <div className="flex items-center space-x-4">
            <button
              onClick={() => setDarkMode(!darkMode)}
              className="p-2 rounded-lg bg-white bg-opacity-20 hover:bg-opacity-30 transition"
            >
              {darkMode ? <Sun size={20} /> : <Moon size={20} />}
            </button>
            <button
              onClick={() => setShowSettings(true)}
              className="p-2 rounded-lg bg-white bg-opacity-20 hover:bg-opacity-30 transition"
            >
              <Settings size={20} />
            </button>
            {notifications.length > 0 && (
              <div className="relative">
                <button className="p-2 rounded-lg bg-white bg-opacity-20 hover:bg-opacity-30 transition">
                  <Bell size={20} />
                </button>
                <span className="absolute -top-1 -right-1 bg-red-500 text-white rounded-full w-5 h-5 text-xs flex items-center justify-center">
                  {notifications.length}
                </span>
              </div>
            )}
          </div>
        </div>
      </div>

      {/* Navigation */}
      <div
        className={`${
          darkMode ? "bg-gray-800 border-gray-700" : "bg-white border-gray-200"
        } shadow-sm border-b`}
      >
        <div className="max-w-7xl mx-auto px-4">
          <div className="flex space-x-1 overflow-x-auto py-2">
            {["dashboard", "orders", "clients", "analytics"].map((view) => (
              <button
                key={view}
                onClick={() => {
                  setCurrentView(view);
                  setShowForm(false);
                  setEditingOrder(null);
                  setShowItemForm(false);
                }}
                className={`px-4 py-2 rounded-lg font-medium transition ${
                  currentView === view
                    ? darkMode
                      ? "bg-blue-900 text-blue-100"
                      : "bg-blue-100 text-blue-700"
                    : darkMode
                    ? "text-gray-300 hover:bg-gray-700"
                    : "text-gray-600 hover:bg-gray-100"
                }`}
              >
                {view === "dashboard" && "📊 Tableau de bord"}
                {view === "orders" && "📦 Commandes"}
                {view === "clients" && "👥 Clients"}
                {view === "analytics" && "📈 Analytics"}
              </button>
            ))}
          </div>
        </div>
      </div>

      <div className="max-w-7xl mx-auto p-4">
        {/* Tableau de bord */}
        {currentView === "dashboard" && (
          <div className="space-y-6">
            {/* Cartes de statistiques */}
            <div className="grid grid-cols-2 md:grid-cols-4 gap-4">
              {[
                {
                  label: "Total Commandes",
                  value: stats.total,
                  icon: Package,
                  color: "blue",
                },
                {
                  label: "En attente",
                  value: stats.pending,
                  icon: Package,
                  color: "orange",
                },
                {
                  label: "Payées",
                  value: stats.paid,
                  icon: DollarSign,
                  color: "green",
                },
                {
                  label: "Chiffre d'affaires",
                  value: `${stats.revenue.toLocaleString()} F`,
                  icon: DollarSign,
                  color: "blue",
                },
              ].map((stat, index) => (
                <div
                  key={index}
                  className={`${cardClasses} p-6 rounded-xl shadow-sm border`}
                >
                  <div className="flex items-center justify-between">
                    <div>
                      <p
                        className={`text-sm ${
                          darkMode ? "text-gray-300" : "text-gray-500"
                        }`}
                      >
                        {stat.label}
                      </p>
                      <p
                        className={`text-3xl font-bold mt-1 ${
                          darkMode
                            ? "text-white"
                            : stat.color === "orange"
                            ? "text-orange-600"
                            : stat.color === "green"
                            ? "text-green-600"
                            : "text-gray-800"
                        }`}
                      >
                        {stat.value}
                      </p>
                    </div>
                    <stat.icon
                      className={
                        stat.color === "orange"
                          ? "text-orange-500"
                          : stat.color === "green"
                          ? "text-green-500"
                          : "text-blue-500"
                      }
                      size={32}
                    />
                  </div>
                </div>
              ))}
            </div>

            {/* Graphiques et meilleurs clients */}
            <div className="grid md:grid-cols-2 gap-6">
              <div className={`${cardClasses} rounded-xl shadow-sm border p-6`}>
                <h3 className="text-xl font-bold mb-4">Revenus récents</h3>
                <div className="space-y-2">
                  {Object.entries(stats.revenueByDay)
                    .slice(0, 7)
                    .map(([date, revenue]) => (
                      <div
                        key={date}
                        className="flex justify-between items-center"
                      >
                        <span
                          className={
                            darkMode ? "text-gray-300" : "text-gray-600"
                          }
                        >
                          {date}
                        </span>
                        <span className="font-bold text-green-600">
                          {revenue.toLocaleString()} F
                        </span>
                      </div>
                    ))}
                </div>
              </div>

              <div className={`${cardClasses} rounded-xl shadow-sm border p-6`}>
                <h3 className="text-xl font-bold mb-4">Meilleurs clients</h3>
                <div className="space-y-3">
                  {stats.topClients.map((client) => (
                    <div
                      key={client.id}
                      className={`p-3 rounded-lg ${
                        darkMode ? "bg-gray-700" : "bg-gray-50"
                      }`}
                    >
                      <div className="flex justify-between items-center">
                        <div>
                          <p className="font-semibold">{client.name}</p>
                          <p
                            className={`text-sm ${
                              darkMode ? "text-gray-400" : "text-gray-500"
                            }`}
                          >
                            {client.totalOrders} commande
                            {client.totalOrders > 1 ? "s" : ""}
                          </p>
                        </div>
                        <span className="font-bold text-blue-600">
                          {client.totalSpent.toLocaleString()} F
                        </span>
                      </div>
                    </div>
                  ))}
                </div>
              </div>
            </div>
          </div>
        )}

        {/* Vue Commandes */}
        {currentView === "orders" && (
          <div className="space-y-4">
            <div className="flex flex-col md:flex-row justify-between items-start md:items-center gap-4">
              <h2 className="text-2xl font-bold">Toutes les commandes</h2>
              <div className="flex flex-wrap gap-2">
                <div
                  className={`relative rounded-lg border ${
                    darkMode ? "border-gray-700" : "border-gray-300"
                  }`}
                >
                  <Search
                    size={20}
                    className="absolute left-3 top-1/2 transform -translate-y-1/2 text-gray-400"
                  />
                  <input
                    type="text"
                    placeholder="Rechercher..."
                    value={searchTerm}
                    onChange={(e) => setSearchTerm(e.target.value)}
                    className={`pl-10 pr-4 py-2 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent ${inputClasses}`}
                  />
                </div>
                <select
                  value={statusFilter}
                  onChange={(e) => setStatusFilter(e.target.value)}
                  className={`px-4 py-2 rounded-lg border focus:ring-2 focus:ring-blue-500 focus:border-transparent ${inputClasses}`}
                >
                  <option value="all">Tous les statuts</option>
                  <option value="pending">En attente</option>
                  <option value="paid">Payé</option>
                  <option value="delivered">Livré</option>
                </select>
                <button
                  onClick={exportToExcel}
                  className="px-4 py-2 bg-green-600 text-white rounded-lg hover:bg-green-700 transition flex items-center space-x-2"
                >
                  <Download size={16} />
                  <span>Export Excel</span>
                </button>
                <button
                  onClick={handleStartOrder}
                  className="bg-blue-600 text-white px-6 py-2 rounded-lg font-semibold flex items-center space-x-2 hover:bg-blue-700 transition shadow-md"
                >
                  <Plus size={20} />
                  <span>Nouvelle commande</span>
                </button>
              </div>
            </div>

            {/* Formulaire de commande - Étape 1: Nombre d'articles */}
            {showForm && !showItemForm && (
              <div className={`${cardClasses} rounded-xl shadow-lg border p-6`}>
                <h3 className="text-xl font-bold mb-4">
                  {editingOrder
                    ? "Modifier la commande"
                    : "Nouvelle commande - Étape 1/2"}
                </h3>
                <div className="space-y-6">
                  <div>
                    <label className="block text-sm font-semibold mb-2">
                      Combien d'articles souhaitez-vous ajouter ? *
                    </label>
                    <input
                      type="number"
                      min="1"
                      max="50"
                      value={itemCount}
                      onChange={(e) =>
                        setItemCount(parseInt(e.target.value) || 1)
                      }
                      className={`w-full px-4 py-3 rounded-lg border focus:ring-2 focus:ring-blue-500 focus:border-transparent ${inputClasses}`}
                      placeholder="Ex: 3"
                    />
                    <p
                      className={`text-sm mt-2 ${
                        darkMode ? "text-gray-400" : "text-gray-500"
                      }`}
                    >
                      Entrez le nombre total d'articles différents pour cette
                      commande
                    </p>
                  </div>

                  <div className="flex gap-3">
                    <button
                      onClick={confirmItemCount}
                      className="flex-1 bg-blue-600 text-white py-3 rounded-lg font-semibold hover:bg-blue-700 transition shadow-md"
                    >
                      Continuer vers les articles →
                    </button>
                    <button
                      onClick={() => {
                        setShowForm(false);
                        setEditingOrder(null);
                      }}
                      className="px-6 py-3 border border-gray-300 rounded-lg font-semibold hover:bg-gray-50 transition"
                    >
                      Annuler
                    </button>
                  </div>
                </div>
              </div>
            )}

            {/* Formulaire de commande - Étape 2: Détails de la commande */}
            {showForm && showItemForm && (
              <div className={`${cardClasses} rounded-xl shadow-lg border p-6`}>
                <h3 className="text-xl font-bold mb-4">
                  {editingOrder
                    ? "Modifier la commande"
                    : "Nouvelle commande - Étape 2/2"}
                </h3>
                <div className="space-y-4">
                  <div className="grid md:grid-cols-3 gap-4">
                    <div>
                      <label className="block text-sm font-semibold mb-2">
                        Nom du client *
                      </label>
                      <input
                        type="text"
                        value={formData.clientName}
                        onChange={(e) =>
                          setFormData({
                            ...formData,
                            clientName: e.target.value,
                          })
                        }
                        className={`w-full px-4 py-2 rounded-lg border focus:ring-2 focus:ring-blue-500 focus:border-transparent ${inputClasses}`}
                        placeholder="Ex: Marie Dupont"
                      />
                    </div>
                    <div>
                      <label className="block text-sm font-semibold mb-2">
                        Téléphone *
                      </label>
                      <input
                        type="tel"
                        value={formData.clientPhone}
                        onChange={(e) =>
                          setFormData({
                            ...formData,
                            clientPhone: e.target.value,
                          })
                        }
                        className={`w-full px-4 py-2 rounded-lg border focus:ring-2 focus:ring-blue-500 focus:border-transparent ${inputClasses}`}
                        placeholder="Ex: 699123456"
                      />
                    </div>
                    <div>
                      <label className="block text-sm font-semibold mb-2">
                        Adresse *
                      </label>
                      <input
                        type="text"
                        value={formData.clientAddress}
                        onChange={(e) =>
                          setFormData({
                            ...formData,
                            clientAddress: e.target.value,
                          })
                        }
                        className={`w-full px-4 py-2 rounded-lg border focus:ring-2 focus:ring-blue-500 focus:border-transparent ${inputClasses}`}
                        placeholder="Ex: Akwa, Douala"
                      />
                    </div>
                  </div>

                  <div>
                    <label className="block text-sm font-semibold mb-2">
                      Notes
                    </label>
                    <textarea
                      value={formData.notes}
                      onChange={(e) =>
                        setFormData({ ...formData, notes: e.target.value })
                      }
                      className={`w-full px-4 py-2 rounded-lg border focus:ring-2 focus:ring-blue-500 focus:border-transparent ${inputClasses}`}
                      placeholder="Notes supplémentaires..."
                      rows="3"
                    />
                  </div>

                  <div className="space-y-3">
                    <div className="flex justify-between items-center">
                      <label className="text-sm font-semibold">
                        Articles ({formData.items.length} article
                        {formData.items.length > 1 ? "s" : ""})
                      </label>
                      <button
                        type="button"
                        onClick={addItem}
                        className="text-blue-600 hover:text-blue-700 font-semibold text-sm flex items-center space-x-1"
                      >
                        <Plus size={16} />
                        <span>Ajouter article</span>
                      </button>
                    </div>
                    {formData.items.map((item, index) => (
                      <div key={index} className="flex gap-2 items-start">
                        <input
                          type="text"
                          value={item.name}
                          onChange={(e) =>
                            updateItem(index, "name", e.target.value)
                          }
                          className={`flex-1 px-4 py-2 rounded-lg border focus:ring-2 focus:ring-blue-500 focus:border-transparent ${inputClasses}`}
                          placeholder={`Nom de l'article ${index + 1}`}
                        />
                        <input
                          type="number"
                          min="1"
                          value={item.quantity}
                          onChange={(e) =>
                            updateItem(index, "quantity", e.target.value)
                          }
                          className="w-20 px-4 py-2 rounded-lg border focus:ring-2 focus:ring-blue-500 focus:border-transparent"
                          placeholder="Qté"
                        />
                        <input
                          type="number"
                          min="0"
                          value={item.price}
                          onChange={(e) =>
                            updateItem(index, "price", e.target.value)
                          }
                          className="w-32 px-4 py-2 rounded-lg border focus:ring-2 focus:ring-blue-500 focus:border-transparent"
                          placeholder="Prix"
                        />
                        {formData.items.length > 1 && (
                          <button
                            type="button"
                            onClick={() => removeItem(index)}
                            className="p-2 text-red-600 hover:bg-red-50 rounded-lg"
                          >
                            <Trash2 size={20} />
                          </button>
                        )}
                      </div>
                    ))}
                  </div>

                  <div
                    className={`p-4 rounded-lg ${
                      darkMode ? "bg-blue-900" : "bg-blue-50"
                    }`}
                  >
                    <p
                      className={`text-lg font-bold ${
                        darkMode ? "text-blue-300" : "text-blue-800"
                      }`}
                    >
                      Total: {calculateTotal(formData.items).toLocaleString()}{" "}
                      FCFA
                    </p>
                  </div>

                  <div className="flex gap-3">
                    <button
                      onClick={handleSubmit}
                      className="flex-1 bg-blue-600 text-white py-3 rounded-lg font-semibold hover:bg-blue-700 transition shadow-md"
                    >
                      {editingOrder
                        ? "Mettre à jour"
                        : "Enregistrer la commande"}
                    </button>
                    <button
                      onClick={() => {
                        setShowForm(false);
                        setShowItemForm(false);
                        setEditingOrder(null);
                      }}
                      className="px-6 py-3 border border-gray-300 rounded-lg font-semibold hover:bg-gray-50 transition"
                    >
                      Annuler
                    </button>
                  </div>
                </div>
              </div>
            )}

            {/* Liste des commandes filtrées */}
            <div className="space-y-3">
              {filteredOrders.length === 0 ? (
                <div
                  className={`${cardClasses} rounded-xl shadow-sm border p-12 text-center`}
                >
                  <Package size={64} className="mx-auto text-gray-300 mb-4" />
                  <p className="text-gray-500 text-lg">
                    Aucune commande trouvée
                  </p>
                  <p className="text-gray-400 mt-2">
                    Ajustez vos filtres ou créez une nouvelle commande
                  </p>
                </div>
              ) : (
                filteredOrders.map((order) => (
                  <div
                    key={order.id}
                    className={`${cardClasses} rounded-xl shadow-sm border p-6`}
                  >
                    <div className="flex justify-between items-start mb-4">
                      <div className="flex-1">
                        <h3 className="text-lg font-bold">
                          {order.clientName}
                        </h3>
                        <p
                          className={`text-sm ${
                            darkMode ? "text-gray-400" : "text-gray-500"
                          }`}
                        >
                          {order.clientPhone} • {order.clientAddress}
                        </p>
                        <p
                          className={`text-xs ${
                            darkMode ? "text-gray-500" : "text-gray-400"
                          } mt-1`}
                        >
                          {new Date(order.date).toLocaleDateString("fr-FR", {
                            day: "numeric",
                            month: "long",
                            year: "numeric",
                            hour: "2-digit",
                            minute: "2-digit",
                          })}
                        </p>
                        {order.notes && (
                          <p
                            className={`text-sm mt-2 p-2 rounded-lg ${
                              darkMode
                                ? "bg-gray-700 text-gray-300"
                                : "bg-gray-100 text-gray-600"
                            }`}
                          >
                            <strong>Note:</strong> {order.notes}
                          </p>
                        )}
                      </div>
                      <StatusBadge status={order.status} />
                    </div>

                    <div
                      className={`rounded-lg p-4 mb-4 ${
                        darkMode ? "bg-gray-700" : "bg-gray-50"
                      }`}
                    >
                      {order.items.map((item, idx) => (
                        <div
                          key={idx}
                          className="flex justify-between text-sm py-1"
                        >
                          <span>
                            {item.name} x{item.quantity}
                          </span>
                          <span className="font-semibold">
                            {(item.quantity * item.price).toLocaleString()} FCFA
                          </span>
                        </div>
                      ))}
                      <div
                        className={`border-t mt-2 pt-2 flex justify-between font-bold ${
                          darkMode ? "border-gray-600" : "border-gray-200"
                        }`}
                      >
                        <span>TOTAL</span>
                        <span className="text-blue-600">
                          {order.total.toLocaleString()} FCFA
                        </span>
                      </div>
                    </div>

                    <div className="flex flex-wrap gap-2">
                      <select
                        value={order.status}
                        onChange={(e) => updateStatus(order.id, e.target.value)}
                        className={`px-4 py-2 rounded-lg border text-sm font-medium focus:ring-2 focus:ring-blue-500 focus:border-transparent ${inputClasses}`}
                      >
                        <option value="pending">En attente</option>
                        <option value="paid">Payé</option>
                        <option value="delivered">Livré</option>
                      </select>
                      <button
                        onClick={() => editOrder(order)}
                        className={`px-4 py-2 rounded-lg transition flex items-center space-x-2 ${
                          darkMode
                            ? "bg-gray-700 text-gray-300 hover:bg-gray-600"
                            : "bg-gray-100 text-gray-700 hover:bg-gray-200"
                        }`}
                      >
                        <Edit2 size={16} />
                        <span>Modifier</span>
                      </button>
                      <button
                        onClick={() => generatePDF(order)}
                        className="px-4 py-2 bg-green-600 text-white rounded-lg hover:bg-green-700 transition flex items-center space-x-2"
                      >
                        <Download size={16} />
                        <span>Facture</span>
                      </button>
                      <button
                        onClick={() => deleteOrder(order.id)}
                        className="px-4 py-2 bg-red-600 text-white rounded-lg hover:bg-red-700 transition flex items-center space-x-2"
                      >
                        <Trash2 size={16} />
                        <span>Supprimer</span>
                      </button>
                    </div>
                  </div>
                ))
              )}
            </div>
          </div>
        )}

        {/* Vue Clients */}
        {currentView === "clients" && (
          <div className={`${cardClasses} rounded-xl shadow-sm border p-6`}>
            <h2 className="text-2xl font-bold mb-6">Gestion des Clients</h2>
            <div className="space-y-4">
              {clients.length === 0 ? (
                <div className="text-center py-8">
                  <User size={64} className="mx-auto text-gray-300 mb-4" />
                  <p className="text-gray-500">Aucun client enregistré</p>
                </div>
              ) : (
                clients.map((client) => (
                  <div
                    key={client.id}
                    className={`p-4 rounded-lg border ${
                      darkMode
                        ? "bg-gray-700 border-gray-600"
                        : "bg-gray-50 border-gray-200"
                    }`}
                  >
                    <div className="flex justify-between items-center">
                      <div>
                        <h3 className="font-bold text-lg">{client.name}</h3>
                        <p
                          className={
                            darkMode ? "text-gray-400" : "text-gray-600"
                          }
                        >
                          {client.phone}
                        </p>
                        <p
                          className={
                            darkMode ? "text-gray-400" : "text-gray-600"
                          }
                        >
                          {client.address}
                        </p>
                      </div>
                      <div className="text-right">
                        <p className="font-bold text-blue-600">
                          {client.totalSpent.toLocaleString()} FCFA
                        </p>
                        <p
                          className={
                            darkMode ? "text-gray-400" : "text-gray-500"
                          }
                        >
                          {client.totalOrders} commande
                          {client.totalOrders > 1 ? "s" : ""}
                        </p>
                      </div>
                    </div>
                  </div>
                ))
              )}
            </div>
          </div>
        )}

        {/* 📊 VUE ANALYTICS AVANCÉE */}
        {currentView === "analytics" && (
          <div className="space-y-6">
            <div className="grid grid-cols-2 md:grid-cols-4 gap-4">
              {[
                {
                  label: "Taux de Conversion",
                  value: `${stats.conversionRate}%`,
                  icon: BarChart3,
                  color: "green",
                },
                {
                  label: "Panier Moyen",
                  value: `${Math.round(
                    stats.averageOrderValue
                  ).toLocaleString()} F`,
                  icon: DollarSign,
                  color: "blue",
                },
                {
                  label: "Revenus Hebdo",
                  value: `${stats.weeklyRevenue.toLocaleString()} F`,
                  icon: Package,
                  color: "orange",
                },
                {
                  label: "Clients Actifs",
                  value: clients.length,
                  icon: Users,
                  color: "purple",
                },
              ].map((stat, index) => (
                <div
                  key={index}
                  className={`${cardClasses} p-6 rounded-xl shadow-sm border`}
                >
                  <div className="flex items-center justify-between">
                    <div>
                      <p
                        className={`text-sm ${
                          darkMode ? "text-gray-300" : "text-gray-500"
                        }`}
                      >
                        {stat.label}
                      </p>
                      <p
                        className={`text-2xl font-bold mt-1 ${
                          darkMode
                            ? "text-white"
                            : stat.color === "orange"
                            ? "text-orange-600"
                            : stat.color === "green"
                            ? "text-green-600"
                            : stat.color === "purple"
                            ? "text-purple-600"
                            : "text-blue-600"
                        }`}
                      >
                        {stat.value}
                      </p>
                    </div>
                    <stat.icon
                      className={
                        stat.color === "orange"
                          ? "text-orange-500"
                          : stat.color === "green"
                          ? "text-green-500"
                          : stat.color === "purple"
                          ? "text-purple-500"
                          : "text-blue-500"
                      }
                      size={32}
                    />
                  </div>
                </div>
              ))}
            </div>

            <div className="grid md:grid-cols-2 gap-6">
              <div className={`${cardClasses} rounded-xl shadow-sm border p-6`}>
                <h3 className="text-xl font-bold mb-4">
                  Articles les Plus Vendus
                </h3>
                <div className="space-y-3">
                  {stats.topItems.length === 0 ? (
                    <p className="text-gray-500 text-center py-4">
                      Aucune donnée disponible
                    </p>
                  ) : (
                    stats.topItems.map((item, index) => (
                      <div
                        key={index}
                        className="flex justify-between items-center p-3 rounded-lg bg-gray-50 bg-opacity-50"
                      >
                        <div className="flex items-center space-x-3">
                          <span className="w-6 h-6 bg-blue-100 text-blue-600 rounded-full text-xs flex items-center justify-center font-bold">
                            {index + 1}
                          </span>
                          <span className="font-medium">{item.name}</span>
                        </div>
                        <span className="font-bold text-blue-600">
                          {item.quantity} vendus
                        </span>
                      </div>
                    ))
                  )}
                </div>
              </div>

              <div className={`${cardClasses} rounded-xl shadow-sm border p-6`}>
                <h3 className="text-xl font-bold mb-4">
                  Répartition des Statuts
                </h3>
                <div className="space-y-4">
                  {Object.entries(stats.ordersByStatus).map(
                    ([status, count]) => (
                      <div
                        key={status}
                        className="flex justify-between items-center"
                      >
                        <span className="capitalize">
                          {status === "pending"
                            ? "En attente"
                            : status === "paid"
                            ? "Payées"
                            : "Livrées"}
                        </span>
                        <div className="flex items-center space-x-3">
                          <div className="w-32 bg-gray-200 rounded-full h-2">
                            <div
                              className={`h-2 rounded-full ${
                                status === "pending"
                                  ? "bg-orange-500"
                                  : status === "paid"
                                  ? "bg-green-500"
                                  : "bg-blue-500"
                              }`}
                              style={{
                                width: `${(count / stats.total) * 100}%`,
                              }}
                            ></div>
                          </div>
                          <span className="font-bold w-8 text-right">
                            {count}
                          </span>
                        </div>
                      </div>
                    )
                  )}
                </div>
              </div>
            </div>

            <div className={`${cardClasses} rounded-xl shadow-sm border p-6`}>
              <h3 className="text-xl font-bold mb-4">Performance Mensuelle</h3>
              <div className="space-y-2">
                {Object.entries(stats.revenueByMonth)
                  .slice(0, 6)
                  .map(([month, revenue]) => (
                    <div
                      key={month}
                      className="flex justify-between items-center py-2 border-b border-gray-200"
                    >
                      <span
                        className={darkMode ? "text-gray-300" : "text-gray-600"}
                      >
                        {month}
                      </span>
                      <span className="font-bold text-green-600">
                        {revenue.toLocaleString()} FCFA
                      </span>
                    </div>
                  ))}
              </div>
            </div>
          </div>
        )}
      </div>

      {/* Modal des paramètres */}
      {showSettings && (
        <div className="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4 z-50">
          <div
            className={`${cardClasses} rounded-xl shadow-2xl max-w-md w-full p-6`}
          >
            <div className="flex justify-between items-center mb-6">
              <h3 className="text-xl font-bold">Paramètres de la boutique</h3>
              <button
                onClick={() => setShowSettings(false)}
                className="p-2 hover:bg-gray-200 rounded-lg"
              >
                <X size={20} />
              </button>
            </div>

            <div className="space-y-4">
              <div>
                <label className="block text-sm font-semibold mb-2">
                  Nom de la boutique
                </label>
                <input
                  type="text"
                  value={shopSettings.name}
                  onChange={(e) =>
                    setShopSettings({ ...shopSettings, name: e.target.value })
                  }
                  className={`w-full px-4 py-2 rounded-lg border focus:ring-2 focus:ring-blue-500 focus:border-transparent ${inputClasses}`}
                />
              </div>

              <div>
                <label className="block text-sm font-semibold mb-2">
                  Téléphone
                </label>
                <input
                  type="text"
                  value={shopSettings.phone}
                  onChange={(e) =>
                    setShopSettings({ ...shopSettings, phone: e.target.value })
                  }
                  className={`w-full px-4 py-2 rounded-lg border focus:ring-2 focus:ring-blue-500 focus:border-transparent ${inputClasses}`}
                />
              </div>

              <div>
                <label className="block text-sm font-semibold mb-2">
                  Adresse
                </label>
                <input
                  type="text"
                  value={shopSettings.address}
                  onChange={(e) =>
                    setShopSettings({
                      ...shopSettings,
                      address: e.target.value,
                    })
                  }
                  className={`w-full px-4 py-2 rounded-lg border focus:ring-2 focus:ring-blue-500 focus:border-transparent ${inputClasses}`}
                />
              </div>

              <div>
                <label className="block text-sm font-semibold mb-2">
                  Signature
                </label>
                <input
                  type="text"
                  value={shopSettings.signature}
                  onChange={(e) =>
                    setShopSettings({
                      ...shopSettings,
                      signature: e.target.value,
                    })
                  }
                  className={`w-full px-4 py-2 rounded-lg border focus:ring-2 focus:ring-blue-500 focus:border-transparent ${inputClasses}`}
                />
              </div>

              <button
                onClick={() => setShowSettings(false)}
                className="w-full bg-blue-600 text-white py-3 rounded-lg font-semibold hover:bg-blue-700 transition"
              >
                Sauvegarder
              </button>
            </div>
          </div>
        </div>
      )}

      {/* Footer avec appel à l'action */}
      <div
        className={`${
          darkMode ? "bg-gray-800 border-gray-700" : "bg-white border-gray-200"
        } border-t mt-8`}
      >
        <div className="max-w-7xl mx-auto py-6 px-4 text-center">
          <p className={`${darkMode ? "text-gray-300" : "text-gray-600"} mb-4`}>
            🚀 <strong>Version Démonstration</strong> - Application 100%
            fonctionnelle
          </p>
          <div className="flex flex-wrap justify-center gap-4">
            <a
              href="wa.me/237657300644"
              className="bg-green-600 text-white px-6 py-2 rounded-lg font-semibold hover:bg-green-700 transition"
            >
              💰 Demander un Devis Personnalisé
            </a>
            <button className="bg-blue-600 text-white px-6 py-2 rounded-lg font-semibold hover:bg-blue-700 transition">
              🔒 Version Sécurisée Disponible
            </button>
            <button className="bg-purple-600 text-white px-6 py-2 rounded-lg font-semibold hover:bg-purple-700 transition">
              📞 Contact: 657300644
            </button>
          </div>
        </div>
      </div>
    </div>
  );
};

export default OrderManagerDemo;

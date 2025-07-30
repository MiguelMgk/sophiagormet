# 🎨 Guia Completo de Personalização - Sophia Gourmet

## 📝 Como Modificar Textos

### 1. Textos Principais
Edite o arquivo `config/site-config.ts`:

\`\`\`typescript
export const siteConfig = {
  brand: {
    name: "SEU NOME AQUI", // Mude o nome da marca
    tagline: "SEU SLOGAN", // Mude o slogan
  },
  hero: {
    title: "SEU TÍTULO",
    subtitle: "SEU SUBTÍTULO",
    description: "SUA DESCRIÇÃO",
  }
}
\`\`\`

### 2. Produtos
No mesmo arquivo, modifique a seção `productsConfig`:

\`\`\`typescript
export const productsConfig = [
  {
    id: 1,
    name: "NOME DO PRODUTO",
    description: "DESCRIÇÃO SENSUAL DO PRODUTO",
    price: 25.90, // Preço em reais
    category: "CATEGORIA",
  }
]
\`\`\`

## 🖼️ Como Adicionar Imagens

### 1. Onde Colocar as Imagens
- Crie a pasta `public/images/` no seu projeto
- Coloque todas as imagens nesta pasta

### 2. Tipos de Imagens Necessárias

#### Produtos (300x300px recomendado):
- `morango-classico.jpg`
- `morango-branco.jpg` 
- `morango-duplo.jpg`
- `morango-castanha.jpg`
- `morango-coco.jpg`
- `morango-supremo.jpg`

#### Clientes (60x60px recomendado):
- `cliente-marina.jpg`
- `cliente-carlos.jpg`
- `cliente-ana.jpg`

#### Banner Principal (1920x1080px recomendado):
- `hero-background.jpg`

### 3. Como Referenciar as Imagens
No arquivo de configuração:

\`\`\`typescript
image: "/images/nome-da-imagem.jpg"
\`\`\`

## 🎨 Como Mudar Cores

### 1. Cores Principais
No arquivo `config/site-config.ts`:

\`\`\`typescript
colors: {
  primary: "blue-600", // Mude para sua cor principal
  primaryHover: "blue-700", // Cor no hover
  secondary: "purple-300", // Cor secundária
}
\`\`\`

### 2. Cores Disponíveis (Tailwind CSS):
- `red-600`, `blue-600`, `green-600`, `purple-600`
- `pink-600`, `indigo-600`, `yellow-600`, `orange-600`
- `gray-600`, `emerald-600`, `teal-600`, `cyan-600`

### 3. Personalizar CSS
Edite `app/globals.css` para cores customizadas:

\`\`\`css
:root {
  --cor-principal: #ff1744; /* Sua cor em hexadecimal */
  --cor-secundaria: #ff8a95;
}
\`\`\`

## 📞 Como Alterar Contato

### WhatsApp
\`\`\`typescript
contact: {
  phone: "5511999999999", // Seu número com código do país
  whatsappMessage: "Sua mensagem personalizada 🍓",
}
\`\`\`

### Redes Sociais
\`\`\`typescript
contact: {
  instagram: "@seuinstagram",
  facebook: "SeuFacebook"
}
\`\`\`

## 🕒 Como Alterar Horários

\`\`\`typescript
schedule: {
  weekdays: "Segunda a Sexta: SEU HORÁRIO",
  weekends: "Sábado e Domingo: SEU HORÁRIO"
}
\`\`\`

## 🎭 Como Personalizar o Estilo

### 1. Fontes
No arquivo `app/layout.tsx`, mude as fontes:

\`\`\`typescript
// Substitua por suas fontes do Google Fonts
href="https://fonts.googleapis.com/css2?family=SuaFonte:wght@400;700&display=swap"
\`\`\`

### 2. Animações
No arquivo `app/globals.css`, adicione suas animações:

\`\`\`css
@keyframes suaAnimacao {
  0% { transform: scale(1); }
  50% { transform: scale(1.1); }
  100% { transform: scale(1); }
}

.sua-classe {
  animation: suaAnimacao 2s infinite;
}
\`\`\`

## 🛠️ Modificações Avançadas

### 1. Adicionar Nova Seção
Crie um novo componente em `components/`:

\`\`\`typescript
// components/nova-secao.tsx
export function NovaSecao() {
  return (
    <section className="py-20">
      <div className="container mx-auto px-4">
        <h2>Sua Nova Seção</h2>
      </div>
    </section>
  )
}
\`\`\`

### 2. Modificar Layout
Edite `app/page.tsx` para alterar a estrutura:

\`\`\`typescript
// Adicione sua nova seção
<NovaSecao />
\`\`\`

## 📱 Responsividade

### Classes Tailwind para Mobile:
- `sm:` - Telas pequenas (640px+)
- `md:` - Telas médias (768px+)  
- `lg:` - Telas grandes (1024px+)
- `xl:` - Telas extra grandes (1280px+)

Exemplo:
\`\`\`typescript
className="text-sm md:text-lg lg:text-xl"
\`\`\`

## 🚀 Dicas de Performance

### 1. Otimizar Imagens
- Use formatos WebP quando possível
- Comprima as imagens antes de usar
- Mantenha tamanhos adequados (não muito grandes)

### 2. Lazy Loading
As imagens já usam lazy loading automático com Next.js

## 🔧 Troubleshooting

### Imagem não aparece?
1. Verifique se está na pasta `public/images/`
2. Confirme o nome do arquivo
3. Use barras normais `/` no caminho

### Cor não muda?
1. Verifique se usou classes Tailwind corretas
2. Limpe o cache do navegador
3. Reinicie o servidor de desenvolvimento

### Texto não atualiza?
1. Salve o arquivo `config/site-config.ts`
2. Verifique se importou corretamente no componente
3. Reinicie o servidor se necessário
\`\`\`

Agora vou atualizar o componente principal para usar as configurações:

```typescriptreact file="app/page.tsx"
[v0-no-op-code-block-prefix]"use client"

import { useState, useEffect } from "react"
import { MapPin, ShoppingCart, Star, Clock, Phone, Instagram, Facebook, X, Menu, Plus, Minus } from 'lucide-react'
import { Button } from "@/components/ui/button"
import { Card, CardContent } from "@/components/ui/card"
import { Select, SelectContent, SelectItem, SelectTrigger, SelectValue } from "@/components/ui/select"
import { Badge } from "@/components/ui/badge"
import { Separator } from "@/components/ui/separator"
import Image from "next/image"
import { saveUserLocation, getUserLocation, clearUserLocation } from "@/lib/location-service"
import { siteConfig, productsConfig, testimonialsConfig } from "@/config/site-config"

interface Product {
  id: number
  name: string
  description: string
  price: number
  image: string
  category: string
}

interface CartItem extends Product {
  quantity: number
}

// Remover a constante products e usar:
const products = productsConfig

// Remover a constante testimonials e usar:
const testimonials = testimonialsConfig

const brazilianStates = [
  "Acre",
  "Alagoas",
  "Amapá",
  "Amazonas",
  "Bahia",
  "Ceará",
  "Distrito Federal",
  "Espírito Santo",
  "Goiás",
  "Maranhão",
  "Mato Grosso",
  "Mato Grosso do Sul",
  "Minas Gerais",
  "Pará",
  "Paraíba",
  "Paraná",
  "Pernambuco",
  "Piauí",
  "Rio de Janeiro",
  "Rio Grande do Norte",
  "Rio Grande do Sul",
  "Rondônia",
  "Roraima",
  "Santa Catarina",
  "São Paulo",
  "Sergipe",
  "Tocantins",
]

export default function SophiaGourmetDelivery() {
  const [currentStep, setCurrentStep] = useState("location") // location, loading, found, site
  const [selectedState, setSelectedState] = useState("")
  const [cart, setCart] = useState<CartItem[]>([])
  const [isCartOpen, setIsCartOpen] = useState(false)
  const [isMobileMenuOpen, setIsMobileMenuOpen] = useState(false)
  const [loadingProgress, setLoadingProgress] = useState(0)
  const [hasStoredLocation, setHasStoredLocation] = useState(false)

  useEffect(() => {
    const checkStoredLocation = async () => {
      const storedLocation = await getUserLocation()
      if (storedLocation) {
        setSelectedState(storedLocation.state)
        setHasStoredLocation(true)
        setCurrentStep("site") // Pular direto para o site se já tem localização
      }
    }
    
    checkStoredLocation()
  }, [])

  // Loading simulation
  useEffect(() => {
    if (currentStep === "loading") {
      const interval = setInterval(() => {
        setLoadingProgress((prev) => {
          if (prev >= 100) {
            clearInterval(interval)
            setTimeout(() => setCurrentStep("found"), 500)
            return 100
          }
          return prev + 2
        })
      }, 40)
      return () => clearInterval(interval)
    }
  }, [currentStep])

  const handleLocationConfirm = async () => {
    if (selectedState) {
      // Salvar no banco de dados
      const saved = await saveUserLocation(selectedState)
      if (saved) {
        console.log('Localização salva com sucesso!')
      }
      
      setCurrentStep("loading")
      setLoadingProgress(0)
    }
  }

  const addToCart = (product: Product) => {
    setCart((prev) => {
      const existing = prev.find((item) => item.id === product.id)
      if (existing) {
        return prev.map((item) => (item.id === product.id ? { ...item, quantity: item.quantity + 1 } : item))
      }
      return [...prev, { ...product, quantity: 1 }]
    })
  }

  const updateQuantity = (id: number, change: number) => {
    setCart((prev) => {
      return prev
        .map((item) => {
          if (item.id === id) {
            const newQuantity = item.quantity + change
            return newQuantity <= 0 ? null : { ...item, quantity: newQuantity }
          }
          return item
        })
        .filter(Boolean) as CartItem[]
    })
  }

  const cartTotal = cart.reduce((sum, item) => sum + item.price * item.quantity, 0)
  const cartItemsCount = cart.reduce((sum, item) => sum + item.quantity, 0)

  const whatsappMessage = encodeURIComponent("Olá, quero pedir um Morango do Amor 🍓")

  // Location Modal
  if (currentStep === "location") {
    return (
      <div className="fixed inset-0 z-50 flex items-center justify-center">
        <div className="absolute inset-0 bg-black/60 backdrop-blur-sm" />
        <div className="relative bg-white rounded-2xl p-8 max-w-md w-full mx-4 shadow-2xl">
          <div className="text-center space-y-6">
            <div className="text-6xl">🍓</div>
            <h2 className="text-2xl font-bold text-gray-800">{siteConfig.location.title}</h2>
            <p className="text-gray-600">{siteConfig.location.description}</p>
            <Select value={selectedState} onValueChange={setSelectedState}>
              <SelectTrigger className="w-full">
                <SelectValue placeholder="Selecione seu estado" />
              </SelectTrigger>
              <SelectContent>
                {brazilianStates.map((state) => (
                  <SelectItem key={state} value={state}>
                    {state}
                  </SelectItem>
                ))}
              </SelectContent>
            </Select>
            <Button
              onClick={handleLocationConfirm}
              disabled={!selectedState}
              className="w-full bg-red-600 hover:bg-red-700 text-white py-3 text-lg font-semibold"
            >
              Confirmar localização
            </Button>
            {hasStoredLocation && (
              <Button
                onClick={async () => {
                  await clearUserLocation()
                  setHasStoredLocation(false)
                  setSelectedState("")
                }}
                variant="outline"
                className="w-full"
              >
                Alterar Localização Salva
              </Button>
            )}
          </div>
        </div>
      </div>
    )
  }

  // Loading Modal
  if (currentStep === "loading") {
    return (
      <div className="fixed inset-0 z-50 flex items-center justify-center bg-white">
        <div className="text-center space-y-8">
          <div className="text-8xl animate-bounce">🍓</div>
          <h2 className="text-2xl font-bold text-gray-800">{siteConfig.location.loadingTitle}</h2>
          <div className="w-80 bg-gray-200 rounded-full h-3">
            <div
              className="bg-red-600 h-3 rounded-full transition-all duration-300 ease-out"
              style={{ width: `${loadingProgress}%` }}
            />
          </div>
          <p className="text-gray-600">{loadingProgress}%</p>
        </div>
      </div>
    )
  }

  // Found Modal
  if (currentStep === "found") {
    return (
      <div className="fixed inset-0 z-50 flex items-center justify-center">
        <div className="absolute inset-0 bg-black/60 backdrop-blur-sm" />
        <div className="relative bg-white rounded-2xl p-8 max-w-md w-full mx-4 shadow-2xl">
          <div className="text-center space-y-6">
            <div className="text-6xl">✨</div>
            <h2 className="text-2xl font-bold text-green-600">{siteConfig.location.foundTitle}</h2>
            <p className="text-gray-700 text-lg leading-relaxed">
              {siteConfig.location.foundDescription}
            </p>
            <p className="text-gray-600">{siteConfig.location.foundCallToAction}</p>
            <Button
              onClick={() => setCurrentStep("site")}
              className="w-full bg-red-600 hover:bg-red-700 text-white py-3 text-lg font-semibold"
            >
              Ver Cardápio
            </Button>
          </div>
        </div>
      </div>
    )
  }

  // Main Site
  return (
    <div className="min-h-screen bg-white">
      {/* Header */}
      <header className="fixed top-0 w-full bg-white/95 backdrop-blur-sm shadow-sm z-40 border-b border-pink-100">
        <div className="container mx-auto px-4 py-4 flex items-center justify-between">
          <h1 className="text-3xl font-bold text-red-600" style={{ fontFamily: "Dancing Script, cursive" }}>
            {siteConfig.brand.name}
          </h1>

          {/* Desktop Navigation */}
          <nav className="hidden md:flex items-center space-x-8">
            <a href="#produtos" className="text-gray-700 hover:text-red-600 transition-colors">
              Produtos
            </a>
            <a href="#depoimentos" className="text-gray-700 hover:text-red-600 transition-colors">
              Depoimentos
            </a>
            <a href="#contato" className="text-gray-700 hover:text-red-600 transition-colors">
              Contato
            </a>
          </nav>

          {/* Cart Button */}
          <div className="flex items-center space-x-4">
            <Button
              onClick={() => setIsCartOpen(true)}
              variant="outline"
              className="relative border-red-200 text-red-600 hover:bg-red-50"
            >
              <ShoppingCart className="w-5 h-5" />
              {cartItemsCount > 0 && (
                <Badge className="absolute -top-2 -right-2 bg-red-600 text-white text-xs">{cartItemsCount}</Badge>
              )}
            </Button>

            {/* Mobile Menu Button */}
            <Button onClick={() => setIsMobileMenuOpen(true)} variant="ghost" size="icon" className="md:hidden">
              <Menu className="w-6 h-6" />
            </Button>
          </div>
        </div>
      </header>

      {/* Mobile Menu */}
      {isMobileMenuOpen && (
        <div className="fixed inset-0 z-50 md:hidden">
          <div className="absolute inset-0 bg-black/50" onClick={() => setIsMobileMenuOpen(false)} />
          <div className="absolute right-0 top-0 h-full w-64 bg-white shadow-xl">
            <div className="p-4 border-b">
              <Button onClick={() => setIsMobileMenuOpen(false)} variant="ghost" size="icon" className="ml-auto">
                <X className="w-6 h-6" />
              </Button>
            </div>
            <nav className="p-4 space-y-4">
              <a href="#produtos" className="block text-gray-700 hover:text-red-600 transition-colors py-2">
                Produtos
              </a>
              <a href="#depoimentos" className="block text-gray-700 hover:text-red-600 transition-colors py-2">
                Depoimentos
              </a>
              <a href="#contato" className="block text-gray-700 hover:text-red-600 transition-colors py-2">
                Contato
              </a>
            </nav>
          </div>
        </div>
      )}

      {/* Hero Banner */}
      <section className="relative h-screen flex items-center justify-center overflow-hidden">
        <div className="absolute inset-0 bg-gradient-to-r from-red-900/80 to-pink-900/80" />
        <Image
          src="/placeholder.svg?height=1080&width=1920"
          alt="Morangos cobertos de chocolate"
          fill
          className="object-cover"
          priority
        />
        <div className="relative z-10 text-center text-white space-y-8 px-4">
          <h2 className="text-4xl md:text-6xl font-bold leading-tight">
            {siteConfig.hero.title}
            <br />
            <span className="text-pink-300">{siteConfig.hero.highlight}</span>
            <span className="text-4xl md:text-5xl"> 🍫🍓</span>
          </h2>
          <p className="text-xl md:text-2xl text-pink-100 max-w-2xl mx-auto">
            {siteConfig.hero.description}
          </p>
          <Button
            size="lg"
            className="bg-red-600 hover:bg-red-700 text-white px-8 py-4 text-xl font-semibold rounded-full shadow-2xl transform hover:scale-105 transition-all"
            onClick={() => document.getElementById("produtos")?.scrollIntoView({ behavior: "smooth" })}
          >
            Pedir Agora
          </Button>
        </div>
      </section>

      {/* Products Section */}
      <section id="produtos" className="py-20 bg-gradient-to-b from-white to-pink-50">
        <div className="container mx-auto px-4">
          <div className="text-center mb-16">
            <h3 className="text-4xl font-bold text-gray-800 mb-4">Nossos Morangos do Amor</h3>
            <p className="text-xl text-gray-600 max-w-2xl mx-auto">
              Cada criação é feita com amor e ingredientes premium para despertar seus sentidos
            </p>
          </div>

          <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
            {products.map((product) => (
              <Card
                key={product.id}
                className="group hover:shadow-2xl transition-all duration-300 transform hover:-translate-y-2 border-pink-100"
              >
                <CardContent className="p-0">
                  <div className="relative overflow-hidden rounded-t-lg">
                    <Image
                      src={product.image || "https://postimg.cc/68DwcZqC"}
                      alt={product.name}
                      width={300}
                      height={300}
                      className="w-full h-64 object-cover group-hover:scale-110 transition-transform duration-300"
                    />
                    <Badge className="absolute top-4 left-4 bg-red-600 text-white">{product.category}</Badge>
                  </div>
                  <div className="p-6 space-y-4">
                    <h4 className="text-xl font-bold text-gray-800">{product.name}</h4>
                    <p className="text-gray-600 leading-relaxed">{product.description}</p>
                    <div className="flex items-center justify-between">
                      <span className="text-2xl font-bold text-red-600">
                        R$ {product.price.toFixed(2).replace(".", ",")}
                      </span>
                      <Button
                        onClick={() => addToCart(product)}
                        className="bg-red-600 hover:bg-red-700 text-white rounded-full px-6"
                      >
                        Adicionar
                      </Button>
                    </div>
                  </div>
                </CardContent>
              </Card>
            ))}
          </div>
        </div>
      </section>

      {/* Testimonials */}
      <section id="depoimentos" className="py-20 bg-white">
        <div className="container mx-auto px-4">
          <div className="text-center mb-16">
            <h3 className="text-4xl font-bold text-gray-800 mb-4">O Que Nossos Clientes Dizem</h3>
            <p className="text-xl text-gray-600">Experiências reais de quem já provou nossos morangos</p>
          </div>

          <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
            {testimonials.map((testimonial, index) => (
              <Card key={index} className="border-pink-100 hover:shadow-lg transition-shadow">
                <CardContent className="p-6 text-center space-y-4">
                  <Image
                    src={testimonial.image || "/placeholder.svg"}
                    alt={testimonial.name}
                    width={60}
                    height={60}
                    className="w-16 h-16 rounded-full mx-auto object-cover"
                  />
                  <div className="flex justify-center space-x-1">
                    {[...Array(testimonial.rating)].map((_, i) => (
                      <Star key={i} className="w-5 h-5 fill-yellow-400 text-yellow-400" />
                    ))}
                  </div>
                  <p className="text-gray-700 italic">"{testimonial.text}"</p>
                  <p className="font-semibold text-gray-800">{testimonial.name}</p>
                </CardContent>
              </Card>
            ))}
          </div>
        </div>
      </section>

      {/* Footer */}
      <footer id="contato" className="bg-gray-900 text-white py-16">
        <div className="container mx-auto px-4">
          <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
            <div className="space-y-4">
              <h4 className="text-2xl font-bold text-red-400" style={{ fontFamily: "Dancing Script, cursive" }}>
                {siteConfig.brand.name}
              </h4>
              <p className="text-gray-300">
                Morangos do amor feitos com carinho e ingredientes premium para momentos especiais.
              </p>
            </div>

            <div className="space-y-4">
              <h5 className="text-lg font-semibold">Horário de Funcionamento</h5>
              <div className="space-y-2 text-gray-300">
                <div className="flex items-center space-x-2">
                  <Clock className="w-4 h-4" />
                  <span>{siteConfig.contact.businessHours.weekdays}</span>
                </div>
                <div className="flex items-center space-x-2">
                  <Clock className="w-4 h-4" />
                  <span>{siteConfig.contact.businessHours.weekend}</span>
                </div>
              </div>
            </div>

            <div className="space-y-4">
              <h5 className="text-lg font-semibold">Contato</h5>
              <div className="space-y-2 text-gray-300">
                <div className="flex items-center space-x-2">
                  <Phone className="w-4 h-4" />
                  <span>{siteConfig.contact.phone}</span>
                </div>
                <div className="flex items-center space-x-2">
                  <MapPin className="w-4 h-4" />
                  <span>{siteConfig.contact.deliveryArea}</span>
                </div>
              </div>
              <div className="flex space-x-4">
                <Instagram className="w-6 h-6 text-pink-400 hover:text-pink-300 cursor-pointer transition-colors" />
                <Facebook className="w-6 h-6 text-blue-400 hover:text-blue-300 cursor-pointer transition-colors" />
              </div>
            </div>
          </div>

          <Separator className="my-8 bg-gray-700" />

          <div className="text-center text-gray-400">
            <p>&copy; 2024 {siteConfig.brand.name}. Todos os direitos reservados.</p>
            <p className="mt-2">Política de Entrega | Termos de Uso | Privacidade</p>
          </div>
        </div>
      </footer>

      {/* Cart Sidebar */}
      {isCartOpen && (
        <div className="fixed inset-0 z-50">
          <div className="absolute inset-0 bg-black/50" onClick={() => setIsCartOpen(false)} />
          <div className="absolute right-0 top-0 h-full w-full max-w-md bg-white shadow-xl">
            <div className="p-4 border-b flex items-center justify-between">
              <h3 className="text-xl font-bold">Seu Carrinho</h3>
              <Button onClick={() => setIsCartOpen(false)} variant="ghost" size="icon">
                <X className="w-6 h-6" />
              </Button>
            </div>

            <div className="flex-1 overflow-y-auto p-4 space-y-4">
              {cart.length === 0 ? (
                <div className="text-center py-8 text-gray-500">
                  <ShoppingCart className="w-16 h-16 mx-auto mb-4 text-gray-300" />
                  <p>Seu carrinho está vazio</p>
                </div>
              ) : (
                cart.map((item) => (
                  <Card key={item.id} className="border-pink-100">
                    <CardContent className="p-4">
                      <div className="flex items-center space-x-4">
                        <Image
                          src={item.image || "/placeholder.svg"}
                          alt={item.name}
                          width={60}
                          height={60}
                          className="w-16 h-16 object-cover rounded-lg"
                        />
                        <div className="flex-1">
                          <h4 className="font-semibold text-sm">{item.name}</h4>
                          <p className="text-red-600 font-bold">R$ {item.price.toFixed(2).replace(".", ",")}</p>
                          <div className="flex items-center space-x-2 mt-2">
                            <Button
                              onClick={() => updateQuantity(item.id, -1)}
                              variant="outline"
                              size="icon"
                              className="w-8 h-8"
                            >
                              <Minus className="w-4 h-4" />
                            </Button>
                            <span className="font-semibold">{item.quantity}</span>
                            <Button
                              onClick={() => updateQuantity(item.id, 1)}
                              variant="outline"
                              size="icon"
                              className="w-8 h-8"
                            >
                              <Plus className="w-4 h-4" />
                            </Button>
                          </div>
                        </div>
                      </div>
                    </CardContent>
                  </Card>
                ))
              )}
            </div>

            {cart.length > 0 && (
              <div className="border-t p-4 space-y-4">
                <div className="flex justify-between items-center text-xl font-bold">
                  <span>Total:</span>
                  <span className="text-red-600">R$ {cartTotal.toFixed(2).replace(".", ",")}</span>
                </div>
                <Button
                  className="w-full bg-red-600 hover:bg-red-700 text-white py-3 text-lg font-semibold"
                  onClick={() => window.open(`https://wa.me/5511999999999?text=${whatsappMessage}`, "_blank")}
                >
                  Finalizar Pedido
                </Button>
              </div>
            )}
          </div>
        </div>
      )}

      {/* WhatsApp Button */}
      <a
        href={`https://wa.me/5511999999999?text=${whatsappMessage}`}
        target="_blank"
        rel="noopener noreferrer"
        className="fixed bottom-6 left-6 bg-green-500 hover:bg-green-600 text-white p-4 rounded-full shadow-2xl transition-all transform hover:scale-110 z-40"
      >
        <Phone className="w-6 h-6" />
      </a>
    </div>
  )
}

# Social Media AI Generator

A powerful AI-driven social media content generation tool for small and medium businesses. Generate platform-optimized content using Claude, OpenAI, and Gemini AI models.

## Features

- 🎯 **Smart Templates** - Pre-built templates for product launches, educational content, behind-the-scenes, testimonials, and promotions
- 🌐 **Multi-Platform Support** - Optimized content for Facebook, Instagram, Twitter/X, LinkedIn, TikTok, YouTube, Pinterest, Snapchat, Reddit, and Discord
- 🤖 **AI Model Comparison** - Compare outputs from Claude 3.5 Sonnet, OpenAI GPT-4, and Google Gemini Pro
- 📋 **Copy-Paste Ready** - Easy content copying with character count tracking
- 🎨 **Dark Professional Theme** - Clean, technical interface optimized for extended use
- 💾 **Content History** - Save and retrieve prompts and outputs using Supabase

## Platform-Specific Features

Each social media platform has built-in:
- Character limits and hashtag limits
- Best posting times
- Platform-specific content rules
- Audience insights
- Optimal content types

## Quick Start

1. **Install dependencies**
   ```bash
   npm install
   ```

2. **Set up environment variables**
   Create a `.env.local` file:
   ```env
   NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
   NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
   OPENAI_API_KEY=your_openai_api_key
   ANTHROPIC_API_KEY=your_anthropic_api_key
   GOOGLE_AI_API_KEY=your_google_ai_api_key
   ```

3. **Set up Supabase database**
   Create the following tables in your Supabase project:

   ```sql
   -- Prompts table
   CREATE TABLE prompts (
     id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
     title TEXT NOT NULL,
     content TEXT NOT NULL,
     platform TEXT NOT NULL,
     business_type TEXT NOT NULL,
     created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
     user_id UUID
   );

   -- Outputs table
   CREATE TABLE outputs (
     id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
     prompt_id UUID REFERENCES prompts(id),
     llm_provider TEXT NOT NULL,
     content TEXT NOT NULL,
     created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
   );
   ```

4. **Run the development server**
   ```bash
   npm run dev
   ```

5. **Open [http://localhost:3000](http://localhost:3000)** in your browser

## How to Use

1. **Select a Template** - Choose from templates like Product Launch, Educational Content, Behind the Scenes, Customer Testimonial, or Promotional Offer

2. **Fill in Details** - Complete the dynamic form fields specific to your chosen template

3. **Choose Platforms** - Select which social media platforms you want to generate content for

4. **Select AI Models** - Choose which AI providers to compare (Claude, OpenAI, Gemini)

5. **Generate Content** - Click generate to create platform-optimized content

6. **Copy and Use** - Copy the generated content directly to your social media platforms

## Technology Stack

- **Frontend**: Next.js 15, React, TypeScript
- **Styling**: Tailwind CSS
- **UI Components**: Custom dark-themed components
- **Database**: Supabase
- **AI Providers**: OpenAI GPT-4, Anthropic Claude 3.5 Sonnet, Google Gemini Pro
- **Icons**: Lucide React

## Business Use Cases

Perfect for:
- Small business owners managing their own social media
- Marketing agencies serving multiple clients
- Content creators needing platform-specific optimization
- Social media managers requiring consistent content creation
- Entrepreneurs launching new products or services

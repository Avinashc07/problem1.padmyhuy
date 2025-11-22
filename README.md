# problem1.padmyhuy
dbuu
import { useEffect } from 'react';
import { useNavigate } from 'react-router-dom';
import { Button } from '@/components/ui/button';
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from '@/components/ui/card';
import { Film, CheckCircle2, Users, Tv, Clapperboard } from 'lucide-react';
import { useAuth } from '@/contexts/AuthContext';

export default function Index() {
  const navigate = useNavigate();
  const { user, loading } = useAuth();

  useEffect(() => {
    if (!loading && user) {
      navigate('/dashboard');
    }
  }, [user, loading, navigate]);

  if (loading) {
    return (
      <div className="min-h-screen flex items-center justify-center bg-gradient-subtle">
        <div className="animate-pulse text-foreground">Loading...</div>
      </div>
    );
  }

  return (
    <div className="min-h-screen bg-gradient-subtle">
      <header className="border-b border-border bg-card shadow-sm">
        <div className="container mx-auto px-4 py-4 flex items-center justify-between">
          <div className="flex items-center gap-3">
            <div className="w-10 h-10 bg-gradient-primary rounded-xl flex items-center justify-center shadow-glow">
              <Film className="w-6 h-6 text-white" />
            </div>
            <h1 className="text-2xl font-bold bg-gradient-primary bg-clip-text text-transparent">
              TV Show Manager
            </h1>
          </div>
          <Button onClick={() => navigate('/auth')}>
            Get Started
          </Button>
        </div>
      </header>

      <main className="container mx-auto px-4 py-16">
        <div className="text-center space-y-6 mb-16">
          <h2 className="text-5xl md:text-6xl font-bold">
            Manage Your
            <span className="block bg-gradient-primary bg-clip-text text-transparent">
              Entertainment Database
            </span>
          </h2>
          <p className="text-xl text-muted-foreground max-w-2xl mx-auto">
            A comprehensive TV show management system with role-based access, complete CRUD operations, and validation.
          </p>
          <Button size="lg" onClick={() => navigate('/auth')} className="shadow-elegant">
            <Film className="mr-2 h-5 w-5" />
            Start Managing Now
          </Button>
        </div>

        <div className="grid gap-8 md:grid-cols-2 lg:grid-cols-3 mb-16">
          <Card className="hover:shadow-glow transition-shadow border-border/50">
            <CardHeader>
              <div className="w-12 h-12 bg-primary/10 rounded-lg flex items-center justify-center mb-4">
                <Tv className="w-6 h-6 text-primary" />
              </div>
              <CardTitle>TV Show Management</CardTitle>
              <CardDescription>
                Create and manage TV shows, seasons, and episodes with detailed tracking
              </CardDescription>
            </CardHeader>
          </Card>

          <Card className="hover:shadow-glow transition-shadow border-border/50">
            <CardHeader>
              <div className="w-12 h-12 bg-secondary/10 rounded-lg flex items-center justify-center mb-4">
                <Users className="w-6 h-6 text-secondary" />
              </div>
              <CardTitle>Cast & Crew</CardTitle>
              <CardDescription>
                Track actors, crew members, screen time, and production roles
              </CardDescription>
            </CardHeader>
          </Card>

          <Card className="hover:shadow-glow transition-shadow border-border/50">
            <CardHeader>
              <div className="w-12 h-12 bg-accent/10 rounded-lg flex items-center justify-center mb-4">
                <Clapperboard className="w-6 h-6 text-accent" />
              </div>
              <CardTitle>Role-Based Access</CardTitle>
              <CardDescription>
                Secure admin and user roles with proper authentication and authorization
              </CardDescription>
            </CardHeader>
          </Card>
        </div>

        <Card className="shadow-elegant border-border/50">
          <CardHeader>
            <CardTitle>Complete Feature Set</CardTitle>
            <CardDescription>Everything you need for TV show management</CardDescription>
          </CardHeader>
          <CardContent>
            <div className="grid md:grid-cols-2 gap-4">
              {[
                'User Authentication & Authorization',
                'Role-Based Access Control (Admin, User)',
                'Complete CRUD Operations',
                'Client & Server-Side Validation',
                'TV Shows, Seasons & Episodes',
                'Cast & Crew Management',
                'Screen Time Tracking',
                'Episode-Crew Assignments',
                'Secure Database with RLS Policies',
                'Modern Responsive UI',
              ].map((feature, index) => (
                <div key={index} className="flex items-start gap-3">
                  <CheckCircle2 className="w-5 h-5 text-success shrink-0 mt-0.5" />
                  <span className="text-foreground">{feature}</span>
                </div>
              ))}
            </div>
          </CardContent>
        </Card>
      </main>

      <footer className="border-t border-border bg-card py-8 mt-16">
        <div className="container mx-auto px-4 text-center text-muted-foreground">
          <p>© 2025 TV Show Manager. Built with modern technologies.</p>
        </div>
      </footer>
    </div>
  );
}
